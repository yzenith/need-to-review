# this file is my personal Django App development flow

1. build up your APP
   1. make sure Django installed ( python -m django --version )
   2. startproject ( django-admin startproject mysite )
   3. about run server ( python manage.py runserver ) # need to excute within manage.py folder
      1. python manage.py runserver 8080  // using 8080
      2. python manage.py runserver 0:8000  // using 0:8000
      3. 会自动重新加载的服务器 runserver 用于开发的服务器在需要的情况下会对每一次的访问请求重新载入一遍 Python 代码。所以你不需要为了让修改代码生效而频繁的重新启动服务器。然而，一些动作，比如添加新文件，将不会触发自动重新加载，这时你得自己手动重启服务器。
   4. start to create your app ( python manage.py startapp polls )

2. write view first
    the view.py is the place to name different page view and process the data then pass to template
    1. example below  
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
    2. use render()
    ```
    polls/views.py¶
    from django.shortcuts import render

    from .models import Question


    def index(request):
        latest_question_list = Question.objects.order_by('-pub_date')[:5]
        context = {'latest_question_list': latest_question_list}
        return render(request, 'polls/index.html', context)
    ``` 

3. write rule in urls.py
    1. the popurse for this file is for visit link
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

    2. You need to add whole apps url to admin
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
4. setup database
    1. 现在，打开 mysite/settings.py 。这是个包含了 Django 项目设置的 Python 模块。

通常，这个配置文件使用 SQLite 作为默认数据库。如果你不熟悉数据库，或者只是想尝试下 Django，这是最简单的选择。Python 内置 SQLite，所以你无需安装额外东西来使用它。当你开始一个真正的项目时，你可能更倾向使用一个更具扩展性的数据库，例如 PostgreSQL，避免中途切换数据库这个令人头疼的问题。

如果你想使用其他数据库，你需要安装合适的 database bindings ，然后改变设置文件中 DATABASES 'default' 项目中的一些键值：

ENGINE -- 可选值有 'django.db.backends.sqlite3'，'django.db.backends.postgresql'，'django.db.backends.mysql'，或 'django.db.backends.oracle'。其它 可用后端。
NAME - 数据库的名称。如果使用的是 SQLite，数据库将是你电脑上的一个文件，在这种情况下， NAME 应该是此文件的绝对路径，包括文件名。默认值 os.path.join(BASE_DIR, 'db.sqlite3') 将会把数据库文件储存在项目的根目录。
如果你不使用 SQLite，则必须添加一些额外设置，比如 USER 、 PASSWORD 、 HOST 等等。想了解更多数据库设置方面的内容，请看文档：DATABASES 。

5. create models, they are the database table
   1. create models
   2. 给模型增加 __str__() 方法是很重要的，这不仅仅能给你在命令行里使用带来方便，Django 自动生成的 admin 里也使用这个方法来表示对象。
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
    3. active models
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
    4. migrate tables
    ```
    $ python manage.py makemigrations polls
    $ python manage.py migrate
    ```
6. practice fetch data from django shell
    ```
    $ python manage.py shell
    ```

7. create a superadmin and add apps to admin panel
   1.  add super uers
   ```
   $ python manage.py createsuperuser
   Username: admin
   Email address: admin@example.com
   Password: **********
   Password (again): *********
   Superuser created successfully.
   ```
   2.  add apps to admin by using register()
   ```
    polls/admin.py¶
    from django.contrib import admin

    from .models import Question

    admin.site.register(Question)
   ```

8. create template
   1. index.html
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
   2. detail.html
    ```
    polls/templates/polls/detail.html¶
    <h1>{{ question.question_text }}</h1>
    <ul>
    {% for choice in question.choice_set.all %}
        <li>{{ choice.choice_text }}</li>
    {% endfor %}
    </ul>
    ```

    2. results.html
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

9.  how to use form properly
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

10. Testing

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

    # run test
    ```
    python manage.py test polls


    # Failed Testing Below
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


    # Succeed Testing Below
    Creating test database for alias 'default'...
    System check identified no issues (0 silenced).
    .
    ----------------------------------------------------------------------
    Ran 1 test in 0.001s

    OK
    Destroying test database for alias 'default'...
    ```