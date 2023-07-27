Bug Report Example for Swallowed Exceptions


To test, please use:


1. For expected Exception being entirely swallowed.
```
query {
  allCategories {
    id
    name
  }
}
```
Expected behavior: Exception with stack trace visible in console.
Actual behavior: No Exception printed to console. Only output: `[27/Jul/2023 08:23:32] "POST /graphql/ HTTP/1.1" 200 143`


2. For unexpected exception being entirely swallowed.
```
query {
  allIngredients {
    id
    name
  }
}
```
Expected behavior: Exception with stack trace visible in console.
Actual behavior: No Exception printed to console. Only output: `[27/Jul/2023 08:24:09] "POST /graphql/ HTTP/1.1" 200 137`


3. For caught exception with print() printing to console.
```
query {
  category {
    id
    name
  }
}
```
Expected behavior: Exception Message printed to console.
Actual behavior: Exception Message printed to console.




Cookbook Example Django Project
===============================

This example project demos integration between Graphene and Django.
The project contains two apps, one named `ingredients` and another
named `recipes`.

Getting started
---------------

First you'll need to get the source of the project. Do this by cloning the
whole Graphene repository:

```bash
# Get the example project code
git clone https://github.com/graphql-python/graphene-django.git
cd graphene-django/examples/cookbook-plain
```

It is good idea (but not required) to create a virtual environment
for this project. We'll do this using
[virtualenv](http://docs.python-guide.org/en/latest/dev/virtualenvs/)
to keep things simple,
but you may also find something like
[virtualenvwrapper](https://virtualenvwrapper.readthedocs.org/en/latest/)
to be useful:

```bash
# Create a virtualenv in which we can install the dependencies
virtualenv env
source env/bin/activate
```

Now we can install our dependencies:

```bash
pip install -r requirements.txt
```

Now setup our database:

```bash
# Setup the database
./manage.py migrate

# Load some example data
./manage.py loaddata ingredients

# Create an admin user (useful for logging into the admin UI
# at http://127.0.0.1:8000/admin)
./manage.py createsuperuser
```

Now you should be ready to start the server:

```bash
./manage.py runserver
```

Now head on over to
[http://127.0.0.1:8000/graphql](http://127.0.0.1:8000/graphql)
and run some queries!
(See the [Graphene-Django Tutorial](http://docs.graphene-python.org/projects/django/en/latest/tutorial-plain/#testing-our-graphql-schema)
for some example queries)

Testing local graphene-django changes
-------------------------------------

In `requirements.txt`, replace the entire `graphene-django=...` line with the following (so that we install the local version instead of the one from PyPI):

```
../../  # graphene-django
```
