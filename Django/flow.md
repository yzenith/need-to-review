# Need to make your python version as 3.7
###This section is about how to use Python3

Use Xcode and brew install python 3.7
xcode-select —install
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

#### for into python3 shell
In venv doing python3
```
python3 -m venv ~/.virtualenvs/myvenv
source ~/.virtualenvs/myvenv/bin/activate
deactivate
```
一般虚拟环境下安装过Django，就不用再安装了。开启就行


# Build Up Your APP
   1.  make sure Django installed ( python -m django --version )
   2.  startproject ( django-admin startproject mysite )
   3.  about run server ( python manage.py runserver ) # need to excute within manage.py folder
      1.  python manage.py runserver 8080  // using 8080
      2.  python manage.py runserver 0:8000  // using 0:8000
      3.  会自动重新加载的服务器 runserver 用于开发的服务器在需要的情况下会对每一次的访问请求重新载入一遍 Python 代码。所以你不需要为了让修改代码生效而频繁的重新启动服务器。然而，一些动作，比如添加新文件，将不会触发自动重新加载，这时你得自己手动重启服务器。
1.  start to create your app ( python manage.py startapp polls )

# Write View First
    the view.py is the place to name different page view and process the data then pass to template
    1. ### example below  
    ```
    polls/views.py¶
    from django.http import HttpResponseRedirect
    from django.shortcuts import get_object_or_404, render
    from django.urls import reverse
    from django.views import generic

    from .models import Choice, Question

    class IndexView(generic.ListView):
        template_name = 'polls/index.html'
        context_object_name = 'latest_question_list'

        def get_queryset(self):
            """Return the last five published questions."""
            return Question.objects.order_by('-pub_date')[:5]


    class DetailView(generic.DetailView):
        model = Question
        template_name = 'polls/detail.html'


    class ResultsView(generic.DetailView):
        model = Question
        template_name = 'polls/results.html'


    def vote(request, question_id):
        ... # same as above, no changes needed.
        
    ```

    1. ### use render()
    ```
    polls/views.py¶
    from django.shortcuts import render

    from .models import Question


    def index(request):
        latest_question_list = Question.objects.order_by('-pub_date')[:5]
        context = {'latest_question_list': latest_question_list}
        return render(request, 'polls/index.html', context)
    ``` 

# write rule in urls.py
    1. ### the popurse for this file is for visit link
    ```
    polls/urls.py
    from django.urls import path

    from . import views

    app_name = 'polls'
    urlpatterns = [
        # ex: /polls/5/
        path('', views.IndexView.as_view(), name='index'),
        path('<int:pk>/', views.DetailView.as_view(), name='detail'),
        path('<int:pk>/results/', views.ResultsView.as_view(), name='results'),
        path('<int:question_id>/vote/', views.vote, name='vote'),
    ]
    ```

# You Need to Add Whole Apps URL to Admin
    ```
    mysite/urls.py¶
    from django.contrib import admin
    from django.urls import include, path

    urlpatterns = [
        path('', views.index, name='index'),
        path('<int:question_id>/', views.detail, name='detail'),
        path('<int:question_id>/results/', views.results, name='results'),
        path('<int:question_id>/vote/', views.vote, name='vote'),
    ]
    ```
# Setup Database
    1. 现在，打开 mysite/settings.py 。这是个包含了 Django 项目设置的 Python 模块。

通常，这个配置文件使用 SQLite 作为默认数据库。如果你不熟悉数据库，或者只是想尝试下 Django，这是最简单的选择。Python 内置 SQLite，所以你无需安装额外东西来使用它。当你开始一个真正的项目时，你可能更倾向使用一个更具扩展性的数据库，例如 PostgreSQL，避免中途切换数据库这个令人头疼的问题。

如果你想使用其他数据库，你需要安装合适的 database bindings ，然后改变设置文件中 DATABASES 'default' 项目中的一些键值：

ENGINE -- 可选值有 'django.db.backends.sqlite3'，'django.db.backends.postgresql'，'django.db.backends.mysql'，或 'django.db.backends.oracle'。其它 可用后端。
NAME - 数据库的名称。如果使用的是 SQLite，数据库将是你电脑上的一个文件，在这种情况下， NAME 应该是此文件的绝对路径，包括文件名。默认值 os.path.join(BASE_DIR, 'db.sqlite3') 将会把数据库文件储存在项目的根目录。
如果你不使用 SQLite，则必须添加一些额外设置，比如 USER 、 PASSWORD 、 HOST 等等。想了解更多数据库设置方面的内容，请看文档：DATABASES 。

# Create Models, They are the Database Table
   1. ### create models
   2. ### 给模型增加 __str__() 方法是很重要的，这不仅仅能给你在命令行里使用带来方便，Django 自动生成的 admin 里也使用这个方法来表示对象。
   ```
    polls/models.py
    from django.db import models


    class Question(models.Model):
        question_text = models.CharField(max_length=200)
        pub_date = models.DateTimeField('date published')
        
        def __str__(self):
        return self.question_text

        def was_published_recently(self):
        return self.pub_date >= timezone.now() - datetime.timedelta(days=1)

    class Choice(models.Model):
        question = models.ForeignKey(Question, on_delete=models.CASCADE)
        choice_text = models.CharField(max_length=200)
        votes = models.IntegerField(default=0)

        def __str__(self):
        return self.choice_text
    ```
# Active Models
    ```
    mysite/settings.py
    INSTALLED_APPS = [
        'polls.apps.PollsConfig',
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
    ]
    ```
# Migrate Tables
    ```
    $ python manage.py makemigrations polls
    $ python manage.py migrate
    ```
# Practice Fetch Data From Django Shell
    ```
    $ python manage.py shell
    ```

# Create a Superadmin and Add Apps to Admin Panel
   1.  ### add super uers
   ```
   $ python manage.py createsuperuser
   Username: admin
   Email address: admin@example.com
   Password: **********
   Password (again): *********
   Superuser created successfully.
   ```
   2.  ### add apps to admin by using register()
   ```
    polls/admin.py¶
    from django.contrib import admin

    from .models import Question

    admin.site.register(Question)
   ```
# create template
   1. ### index.html
   ```
   polls/templates/polls/index.html¶
    {% if latest_question_list %}
        <ul>
        {% for question in latest_question_list %}
            <li><a href="{% url 'polls:detail' question.id %}">{{ question.question_text }}</a></li>
        {% endfor %}
        </ul>
    {% else %}
        <p>No polls are available.</p>
    {% endif %}
   ```
   1. ### detail.html
    ```
    polls/templates/polls/detail.html¶
    <h1>{{ question.question_text }}</h1>
    <ul>
    {% for choice in question.choice_set.all %}
        <li>{{ choice.choice_text }}</li>
    {% endfor %}
    </ul>
    ```

    1. ### results.html
   ```
   polls/templates/polls/results.html¶
    <h1>{{ question.question_text }}</h1>

    <ul>
    {% for choice in question.choice_set.all %}
        <li>{{ choice.choice_text }} -- {{ choice.votes }} vote{{ choice.votes|pluralize }}</li>
    {% endfor %}
    </ul>

    <a href="{% url 'polls:detail' question.id %}">Vote again?</a>
    ```

# How to Use Form Properly

    ```
    polls/templates/polls/detail.html¶
    <h1>{{ question.question_text }}</h1>

    {% if error_message %}<p><strong>{{ error_message }}</strong></p>{% endif %}

    <form action="{% url 'polls:vote' question.id %}" method="post">
    {% csrf_token %}
    {% for choice in question.choice_set.all %}
        <input type="radio" name="choice" id="choice{{ forloop.counter }}" value="{{ choice.id }}">
        <label for="choice{{ forloop.counter }}">{{ choice.choice_text }}</label><br>
    {% endfor %}
    <input type="submit" value="Vote">
    </form>
    ```



# Testing

    ```
    # confirm the future published post won't show in recently posts
    polls/tests.py¶
    import datetime

    from django.test import TestCase
    from django.utils import timezone

    from .models import Question


    class QuestionModelTests(TestCase):

        def test_was_published_recently_with_future_question(self):
            """
            was_published_recently() returns False for questions whose pub_date
            is in the future.
            """
            time = timezone.now() + datetime.timedelta(days=30)
            future_question = Question(pub_date=time)
            self.assertIs(future_question.was_published_recently(), False)
    ```

### Run Test
    ```
    python manage.py test polls
    ```


### Failed Testing Below
    ```
    System check identified no issues (0 silenced).
    F
    ======================================================================
    FAIL: test_was_published_recently_with_future_question (polls.tests.QuestionModelTests)
    ----------------------------------------------------------------------
    Traceback (most recent call last):
    File "/path/to/mysite/polls/tests.py", line 16, in test_was_published_recently_with_future_question
        self.assertIs(future_question.was_published_recently(), False)
    AssertionError: True is not False

    ----------------------------------------------------------------------
    Ran 1 test in 0.001s

    FAILED (failures=1)
    Destroying test database for alias 'default'...
    ```

### Succeed Testing Below
    ```
    Creating test database for alias 'default'...
    System check identified no issues (0 silenced).
    .
    ----------------------------------------------------------------------
    Ran 1 test in 0.001s

    OK
    Destroying test database for alias 'default'...
    ```

### View Testing

#### 第一步是在 shell 中配置测试环境:
    ```
    $ python manage.py shell
    ```
#### Shell Setup
    ```
    >>> from django.test.utils import setup_test_environment
    >>> setup_test_environment()
    ```

#### 然后我们需要导入 django.test.TestCase 类（在后续 tests.py 的实例中我们将会使用 django.test.TestCase 类，这个类里包含了自己的 client 实例，所以不需要这一步）:
    ```
    >>> from django.test import Client
    >>> # create an instance of the client for our use
    >>> client = Client()
    ```
#### 搞定了之后，我们可以要求 client 为我们工作了:
    ```
    >>> # get a response from '/'
    >>> response = client.get('/')
    Not Found: /
    >>> # we should expect a 404 from that address; if you instead see an
    >>> # "Invalid HTTP_HOST header" error and a 400 response, you probably
    >>> # omitted the setup_test_environment() call described earlier.
    >>> response.status_code
    404
    >>> # on the other hand we should expect to find something at '/polls/'
    >>> # we'll use 'reverse()' rather than a hardcoded URL
    >>> from django.urls import reverse
    >>> response = client.get(reverse('polls:index'))
    >>> response.status_code
    200
    >>> response.content
    b'\n    <ul>\n    \n        <li><a href="/polls/1/">What&#x27;s up?</a></li>\n    \n    </ul>\n\n'
    >>> response.context['latest_question_list']
    <QuerySet [<Question: What's up?>]>
    ```

### TEST the View.py

#### Adding following code
```
polls/tests.py¶
from django.urls import reverse
```

#### 然后我们写一个公用的快捷函数用于创建投票问题，再为视图创建一个测试类：

```
polls/tests.py¶
def create_question(question_text, days):
    """
    Create a question with the given `question_text` and published the
    given number of `days` offset to now (negative for questions published
    in the past, positive for questions that have yet to be published).
    """
    time = timezone.now() + datetime.timedelta(days=days)
    return Question.objects.create(question_text=question_text, pub_date=time)


class QuestionIndexViewTests(TestCase):
    def test_no_questions(self):
        """
        If no questions exist, an appropriate message is displayed.
        """
        response = self.client.get(reverse('polls:index'))
        self.assertEqual(response.status_code, 200)
        self.assertContains(response, "No polls are available.")
        self.assertQuerysetEqual(response.context['latest_question_list'], [])

    def test_past_question(self):
        """
        Questions with a pub_date in the past are displayed on the
        index page.
        """
        create_question(question_text="Past question.", days=-30)
        response = self.client.get(reverse('polls:index'))
        self.assertQuerysetEqual(
            response.context['latest_question_list'],
            ['<Question: Past question.>']
        )

    def test_future_question(self):
        """
        Questions with a pub_date in the future aren't displayed on
        the index page.
        """
        create_question(question_text="Future question.", days=30)
        response = self.client.get(reverse('polls:index'))
        self.assertContains(response, "No polls are available.")
        self.assertQuerysetEqual(response.context['latest_question_list'], [])

    def test_future_question_and_past_question(self):
        """
        Even if both past and future questions exist, only past questions
        are displayed.
        """
        create_question(question_text="Past question.", days=-30)
        create_question(question_text="Future question.", days=30)
        response = self.client.get(reverse('polls:index'))
        self.assertQuerysetEqual(
            response.context['latest_question_list'],
            ['<Question: Past question.>']
        )

    def test_two_past_questions(self):
        """
        The questions index page may display multiple questions.
        """
        create_question(question_text="Past question 1.", days=-30)
        create_question(question_text="Past question 2.", days=-5)
        response = self.client.get(reverse('polls:index'))
        self.assertQuerysetEqual(
            response.context['latest_question_list'],
            ['<Question: Past question 2.>', '<Question: Past question 1.>']
        )
```

# Adding the CSS and Javascript for your APPS
#### 首先，在你的 polls 目录下创建一个名为 static 的目录。Django 将在该目录下查找静态文件，这种方式和 Diango 在 polls/templates/ 目录下查找 template 的方式类似。

#### Within the static directory you have just created, create another directory called polls and within that create a file called style.css. In other words, your stylesheet should be at polls/static/polls/style.css. Because of how the AppDirectoriesFinder staticfile finder works, you can refer to this static file in Django as polls/style.css, similar to how you reference the path for templates.

### 将以下代码放入样式表(polls/static/polls/style.css)：
```
polls/static/polls/style.css¶
li a {
    color: green;
}
```
### 下一步，在 polls/templates/polls/index.html 的文件头添加以下内容：
```
polls/templates/polls/index.html¶
{% load static %}

<link rel="stylesheet" type="text/css" href="{% static 'polls/style.css' %}">
```

# 自定义后台表单¶
#### 通过 admin.site.register(Question) 注册 Question 模型，Django 能够构建一个默认的表单用于展示。通常来说，你期望能自定义表单的外观和工作方式。你可以在注册模型时将这些设置告诉 Django。让我们通过重排列表单上的字段来看看它是怎么工作的。用以下内容替换 admin.site.register(Question)：
```
polls/admin.py¶
from django.contrib import admin

from .models import Question


class QuestionAdmin(admin.ModelAdmin):
    fields = ['pub_date', 'question_text']

admin.site.register(Question, QuestionAdmin)
```

#### 这在只有两个字段时显得没啥卵用，但对于拥有数十个字段的表单来说，为表单选择一个直观的排序方法就显得你的针很细了。说到拥有数十个字段的表单，你可能更期望将表单分为几个字段集：
```
polls/admin.py¶
from django.contrib import admin

from .models import Question


class QuestionAdmin(admin.ModelAdmin):
    fieldsets = [
        (None,               {'fields': ['question_text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]

admin.site.register(Question, QuestionAdmin)
```

## 添加关联的对象¶
#### 好了，现在我们有了投票的后台页。不过，一个 Question 有多个 Choice，但后台页却没有显示多个选项。好了。There are two ways to solve this problem. The first is to register Choice with the admin just as we did with Question:
```
polls/admin.py¶
from django.contrib import admin

from .models import Choice, Question
# ...
admin.site.register(Choice)
```
## 移除调用 register() 注册 Choice 模型的代码。随后，像这样修改 Question 的注册代码：这会告诉 Django：“Choice 对象要在 Question 后台页面编辑。默认提供 3 个足够的选项字段。”
```
polls/admin.py¶
from django.contrib import admin

from .models import Choice, Question


class ChoiceInline(admin.StackedInline):
    model = Choice
    extra = 3


class QuestionAdmin(admin.ModelAdmin):
    fieldsets = [
        (None,               {'fields': ['question_text']}),
        ('Date information', {'fields': ['pub_date'], 'classes': ['collapse']}),
    ]
    inlines = [ChoiceInline]

admin.site.register(Question, QuestionAdmin)
```
#### One small problem, though. It takes a lot of screen space to display all the fields for entering related Choice objects. For that reason, Django offers a tabular way of displaying inline related objects. To use it, change the ChoiceInline declaration to read:
```
polls/admin.py¶
class ChoiceInline(admin.TabularInline):
    #...
```
#### 默认情况下，Django 显示每个对象的 str() 返回的值。但有时如果我们能够显示单个字段，它会更有帮助。为此，使用 list_display 后台选项，它是一个包含要显示的字段名的元组，在更改列表页中以列的形式展示这个对象：
```
polls/admin.py¶
class QuestionAdmin(admin.ModelAdmin):
    # ...
    list_display = ('question_text', 'pub_date', 'was_published_recently')
```

#### 你可以点击列标题来对这些行进行排序——除了 was_published_recently 这个列，因为没有实现排序方法。顺便看下这个列的标题 was_published_recently，默认就是方法名（用空格替换下划线），该列的每行都以字符串形式展示出处。你可以通过给这个方法（在 polls/models.py 中）一些属性来达到优化的目的，像这样：

```
polls/models.py¶
class Question(models.Model):
    # ...
    def was_published_recently(self):
        now = timezone.now()
        return now - datetime.timedelta(days=1) <= self.pub_date <= now
    was_published_recently.admin_order_field = 'pub_date'
    was_published_recently.boolean = True
    was_published_recently.short_description = 'Published recently?'
```

### 再次编辑文件 polls/admin.py，优化 Question 变更页：过滤器，使用 list_filter。将以下代码添加至 QuestionAdmin：展示的过滤器类型取决你你要过滤的字段的类型。因为 pub_date 是类 DateTimeField，Django 知道要提供哪个过滤器：“任意时间”，“今天”，“过去7天”，“这个月”和“今年”。
```
list_filter = ['pub_date']
```

### 在列表的顶部增加一个搜索框。当输入待搜项时，Django 将搜索 question_text 字段。你可以使用任意多的字段——由于后台使用 LIKE 来查询数据，将待搜索的字段数限制为一个不会出问题大小，会便于数据库进行查询操作。

```
search_fields = ['question_text']
```

# 自定义你的 工程的 模板
### 在你的工程目录（指包含 manage.py 的那个文件夹）内创建一个名为 templates 的目录。模板可放在你系统中任何 Django 能找到的位置。（谁启动了 Django，Django 就以他的用户身份运行。）不过，把你的模板放在工程内会带来很大便利，推荐你这样做。打开你的设置文件（mysite/settings.py，牢记），在 TEMPLATES 设置中添加 DIRS 选项

```
mysite/settings.py¶
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'templates')],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```