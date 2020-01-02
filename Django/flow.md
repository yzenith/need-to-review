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
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, world. You're at the polls index.")
   ```

3. write rule in urls.py
    1. the popurse for this file is for visit link
    ```
    polls/urls.py
    from django.urls import path

    from . import views

    urlpatterns = [
        path('', views.index, name='index'),
    ]
    ```

    1. You need to add whole apps url to admin
    ```
    mysite/urls.py¶
    from django.contrib import admin
    from django.urls import include, path

    urlpatterns = [
        path('polls/', include('polls.urls')),
        path('admin/', admin.site.urls),
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
   ```
    polls/models.py
    from django.db import models


    class Question(models.Model):
        question_text = models.CharField(max_length=200)
        pub_date = models.DateTimeField('date published')


    class Choice(models.Model):
        question = models.ForeignKey(Question, on_delete=models.CASCADE)
        choice_text = models.CharField(max_length=200)
        votes = models.IntegerField(default=0)
    ```
    2. active models
    ```
    mysite/settings.py¶
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
    3. migrate tables
    ```
    $ python manage.py makemigrations polls
    ```
6. 