#Django-Drupal Password Hasher

## Introduction

Django-Drupal Password Hasher is a simple package created to hash Drupal 7 passwords with the prefix 'drupal'

Taken from https://djangosnippets.org/snippets/3030/ and modified

## Installation

Available at https://pypi.python.org/pypi/Django-Drupal-Password-Hasher

In your virtualenv

    pip install Django-Drupal-Password-Hasher     

Add the following line to your settings.py file in the "PASSWORD_HASHERS" section

    'djangodrupalpasswordhasher.drupal_password_hasher.DrupalPasswordHasher',

OR

Copy the necessary files into your django project
In your django home directory

    ./managy.py startapp utils
    mv utils project_name/
    mv path/to/djangodrupalpasswordhasher/drupal_password_hasher.py project_name/utils/__init__.py
    mv path/to/djangodrupalpasswordhasher/test/test_drupal_password_hasher.py project_name/utils/tests.py

Add the application to your project and your password hasher list in the settings.py file

    INSTALLED_APPS = (
        ...
        'project_name.utils',
        ...
    )

    PASSWORD_HASHERS = (
        ...
        'project_name.utils.DrupalPasswordHasher',
        ...
    )

## Usage

User authentication stays the same

    from django.contrib.auth.models import User

    ...

    user = User(first_name='foo', last_name='bar', email='foobar@foobar.com')
    user.set_password("some_random_password")
    user.save()

Note: Django uses the first entry in the PASSWORD_HASHERS section of your settings file for user authentication by default. If you have other password hashers but want to use this one, make sure it is the first entry in the list.
