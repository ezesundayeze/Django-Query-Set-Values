# Django-Query-Set-Values
## Django Query Set values and how to use them

1. ## exact
#### How to use the exact keyword to query your database

 Let's assume we have a model (Food). I actually love food pardon my manners.


```python
class Food(models.Model):
    food_id =  models.IntegerField()
    name = models.CharField(max_length=200)
```


I'm going to limit it to only the name and id id field for this example. We'll add more fields if necessary for other examples.

So, let's get down to business.

Define a function and Set your query string variable:

```python
from .models import Food

def home(request):
    food = request['food']
    getFood = Food.objects.filter(name__exact=food)
    return render(request, urlPath)
```

For this query, you are querying the Food table to retrieve results that match exactly what the user enters into the input field. That means, if what is in the database is "Afang Soup" if the user searches for "AFanG SOuP", "afang souP, "AFANG SOUP", "Afang soup" or anything other than "Afang Soup", it'll return an empty list

If nothing matches the string, an emapty list will be returned.

Notice that I'm using double underscore. if use anything other than that it won't work.


2. ## iexact
### How to use iexact

iexact is similar to exact. The only difference is that it capitalization doesn't matter here.
"Afang Soup" will equal "afang soup", "AFANG SOUP", etc.


```python
from .models import Food

def home(request):
    food = request['food']
    getFood = Food.objects.filter(name__iexact=food)
    return render(request, urlPath)
```

As a rule of thumb, just know that each time you add "i" to the some of the query sets, you are saying it should ignore capitalization 

3. contains


"contains", like the name implies checks if a string is contained in the table being queried. So, imagine we have




1. icontains
1. in
1. gt
1. gte
1. lt
1. lte
1. startswith
1. istartswith
1. endswith
1. iendswith
1. range
1. year
1. month
1. day
1. week_day
1. isnull
1. search
1. regex
1. iregex
