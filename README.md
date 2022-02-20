# Bracken Pen Turners - An E-commerce Store

## Milestone Project 4



- [**About**](#About)
- [**UX**](#UX)
  - [User Stories](#User-Stories)
  - [Research](#Research)
  - [Styling](#Styling)
  - [Wireframes](#Wireframes)
- [**Features**](#Features)
  - [Functionality](#Functionality)
  - [Existing Features](#Existing-Features)
    - [Game Controls](#Game-Controls)
  - [Features Left To Implement](#Features-Left-To-Implement)
- [**Technologies Used**](#Technologies-Used)
  - [Version Control](#Version-Control)
- [**Testing**](#Testing)
  - [Testing User Stories](#Testing-User-Stories)
  - [Responsive Testing](#Responsive-Testing)
  - [Additional Testing](#Additional-Testing)
  - [HTML And CSS Validation](#HTML-And-CSS-Validation)
  - [Interesting Bugs Or Problems](#Interesting-Bugs-Or-Problems)
- [**Deployment**](#Deployment)
  - [Running Code Locally](#Running-Code-Locally)
- [**Credits**](#Credits)
  - [Content](#Content)
    
  - [Acknowledgements](#Acknowledgements)
  - [Disclaimer](#Disclaimer)


## About

Bracken Pen Turner, 

## UX

### User Stories

- Shopper
    - View Items for sale
    - Search items for sale
    - See individual item details
    - see all items for sale
    - able to view the total of your current purchases.

- Site Browser
    - Rigester for an account
    - able to log in and log out
    - recvoery of forgotten password
    - personalised profile

- sorting and searching
    - Sort the list of available products
    - sort a specific
    - sort multiple categories of products simltaneously
    - Search for a product be name or description
    - Easily see what was search for and number of results. 

- Purchasing and checkout
    - 


## Styling

The chosen font was the one Roy used to design his logo, which was Calibra Light, when I looked to google fonts, I found Open Sans to be most like it, so I elected that as the backup with calibra as the primary font. 

[Google fonts](https://fonts.google.com/specimen/Lato?query=lato&selection.family=Lato&sidebar.open=)

Font awesome was used to provide the icons, that really bring the page to life. 

[Font Awesome](https://fontawesome.com/kits/e5ebf0ee99/use                                                                                                                                                                                                                                                                                      )

### Deployment.

#### Github, Gitpod, Git, Heroku, and Amazon AWS.

- #### Project setup.
 - The project was set up on GitHub using the Code Institue Gitpod Template.
  - I located the template on the Code Institute GitHub page and clicked the use template button.
  - I then named my repository and created it.
  - Once the repository was created I was able to open it with Gitpod.
  - I could then use the terminal to create files and folders and start coding the project.
  - Throughout the project, I used git to add my changes to version control in GitHub.
  - To commit I added the file to the staging area with the 
    ```
        git add <filename>
    ```
    ```
        git commit -m "<commit message>"
    ```
    ```
        git push
    ```


- #### Installing Django
    ```
       pip3 install Django==3.2
    ```
- create project folder

    ```
       django-admin startproject bracken_pen .
    ```

- create file: 

    ```
      touch .gitignore      
    ```

- To run the programe
  ```
    python3 manage.py runserver
  ```

- This should show the install has worked but there will be migrations to take care off. 
  ```
    python3 manage.py migrate
  ```

-It would now be useful to create a super user
  ```
    python3 manage.py createsuperuser
  ```

- To enable user function use django allauth
  ```
  pip3 install django-allauth==0.41.0
  ```

  [full allauth documtation](https://django-allauth.readthedocs.io/en/latest/installation.html)

- to create a requirement file
  ```
    pip3 freeze > requirements.txt
  ```

- to create the alluth templates folder contents
  ```
  cp -r ../.pip-modules/lib/python3.8/site-packages/allauth/templates/* ./templates/allauth/
  ```



-to add the products section
 
 ```
 python3 manage.py startapp products
 ```

-add the app to setting.py

```
mkdir products/fixtures
```

-to add the bag

```
python3 manage.py startapp bag
```

- to add the checkout section
```
python3 manage.py startapp checkout
```
once the code is written, look to make the migrations.
```
python3 manage.py makemigrations --dry-run
```
```
python3 manage.py makemigrations
```
```
python3 manage.py migrate --plan
```

- crispy forms for checkout
```
pip3 install django-crispy-forms
```

- also a good time to updatethe requirements file
```
pip3 freeze > requirements.txt
```

-Connecting to Stripe

first create an account with [stripe](https://stripe.com/gb)

remember to confirm it by clicking on the email from Stripe. 

first add their JS to the core js block in the base template.
```
<head>
  <title>Checkout</title>
  <script src="https://js.stripe.com/v3/"></script>
</head>
```
then add it to the checkout.html with post block
```
{% block postloadjs %}
    {{ block.super }}
    {{ stripe_public_key|json_script:"id_stripe_public_key" }}
    {{ client_secret|json_script:"id_client_secret" }}
    <script src="{% static 'checkout/js/stripe_elements.js' %}"></script>
{% endblock %}
```

add js to the checkout js
```
/*
    Core logic/payment flow for this comes from here:
    https://stripe.com/docs/payments/accept-a-payment
    CSS from here: 
    https://stripe.com/docs/stripe-js
*/

var stripe_public_key = $('#id_stripe_public_key').text().slice(1, -1);
var client_secret = $('#id_client_secret').text().slice(1, -1);
var stripe = Stripe(stripe_public_key);
var elements = stripe.elements();
var style = {
    base: {
        color: '#000',
        fontFamily: '"Helvetica Neue", Helvetica, sans-serif',
        fontSmoothing: 'antialiased',
        fontSize: '16px',
        '::placeholder': {
            color: '#aab7c4'
        }
    },
    invalid: {
        color: '#dc3545',
        iconColor: '#dc3545'
    }
};
var card = elements.create('card', {style: style});
card.mount('#card-element');
```

add css to the css file
```
.StripeElement--focus,
.stripe-style-input:focus,
.stripe-style-input:active {
  box-shadow: 0 1px 3px 0 #cfd7df;
}

.StripeElement--webkit-autofill {
  background-color: #fefde5 !important;
}

.stripe-style-input::placeholder {
    color: #aab7c4;
}

.fieldset-label {
    position: relative;
    right: .5rem;
}

#payment-form .form-control,
#card-element {
    color: #000;
    border: 1px solid #000;
}
```

then add the public key to checkout views.py context

then install stripe via the terminal
```
pip3 install stripe
```

import it to view.py



installing countries to checkout. 

```
pip3 install django-countries
```

update 



Deployement to heroku

log onto [Heroku](https://dashboard.heroku.com/)

click on create new app. 

name it and click on the region closest to you. 

<img src="/workspace/BrackenPenTurner/ReadMePics/deployement/new app .jpg" alt="image of ">

then click on resources, 

in add on type 

```
postgres
```

<img src="/workspace/BrackenPenTurner/ReadMePics/deployement/resourcePostgress.jpg">

chose the free plan, 

<img src="/workspace/BrackenPenTurner/ReadMePics/deployement/freePlan.jpg">


you shoould then see the following:

<img src="/workspace/BrackenPenTurner/ReadMePics/deployement/postgreInstalled.jpg">

once that is done go back to gitpod cli and install 

```
pip3 install dj_database_url

```

then install
```
pip3 install psycopg2-binary
```


then freeze requirements. 
```
pip3 freeze > requirements.txt
```

<img src="/workspace/BrackenPenTurner/ReadMePics/deployement/requirementsTxtView.jpg">


once that is done, goto settings.py in the project folder. 

add 
```
import dj_database_url
```

comment out the default database setting. line circa 119

```
# Database
# https://docs.djangoproject.com/en/3.2/ref/settings/#databases

#DATABASES = {
#    'default': {
#        'ENGINE': 'django.db.backends.sqlite3',
#        'NAME': BASE_DIR / 'db.sqlite3',
#    }
#}
```

Replace it with, 

```
DATABASES = {
    'default': dj_database_url.parse(url)
}
```
You'll need to add the database url from heroku, this is found here:

<img src="/workspace/BrackenPenTurner/ReadMePics/deployement/configVars.jpg">


Now you'll need to run migrations all over again. 

```
python3 manage.py showmigration
```

<img src="/workspace/BrackenPenTurner/ReadMePics/deployement/showMigrations.jpg">


the run

```
python3 manage.py migrate
```

<img src="/workspace/BrackenPenTurner/ReadMePics/deployement/mirgate.jpg">

then import product data. 

```
python3 manage.py loaddata categories
```

<img src="/workspace/BrackenPenTurner/ReadMePics/deployement/loadCategories.jpg">

```
python3 manage.py loaddata products
```
<img src="/workspace/BrackenPenTurner/ReadMePics/deployement/loadProducts.jpg">

the is important, categories first then products. 

Now create the super user
```
python3 manage
```

a side note if you didn't use fixtures. 

```
A note for creating your database if you didn't use fixtures
When you come to follow this process for your milestone project, you may not have used a fixtures file to populate your database like the instructor did.

If this is the case, manually re-creating your database when you come to deploy can take a considerable amount of time. Thankfully, there is a short process you can follow to download your local mysql database and then upload it to postgres:

Make sure your manage.py file is connected to your mysql database
Use this command to backup your current database and load it into a db.json file:
python3 manage.py dumpdata --exclude auth.permission --exclude contenttypes > db.json
Connect your manage.py file to your postgres database
Then use this command to load your data from the db.json file into postgres:
python3 manage.py loaddata db.json
```




aws - s3 - simple storgae service. 




### Repository Link

To run the site in a live environment [click here](http://claims-corner.herokuapp.com/login)

The link to my repository can be found via this link:
[Link to Repository](https://github.com/whatnote/BrackenPenTurner)

### Content

- I followed the course "Boutique Ado" and code for project was lifted from the putting it all together from the [Backend Developenment course from the CODE Institute](https://learn.codeinstitute.net/courses/course-v1:CodeInstitute+FSF_102+Q1_2020/courseware/4201818c00aa4ba3a0dae243725f6e32/d3188bf68530497aa5fba55d07a9d7d7/), 
  
  
  Particularly the:

  -  register 
  -  logon 
  -  log off 

  we're lifted directly from the course with just minor amendments to the CSS and html. 

the claims list was mapped accross from the task list. as was the 
- new claim 
- edit and delete feature
- search 

In these particulary cases the code was amended to suite to the requirement of the user stories. 

the email connenction was lifted from the codeinstitute course. 
#### Putting it all toghter - Sending email using emailJS [link to course here](https://learn.codeinstitute.net/courses/course-v1:CodeInstitute+IFD101+2017_T3/courseware/03d3f6524ad249d9b33e3336d156dfd0/e4710f80cdf34bffbd607bc102482d5c/)



## Technologies-Used

[**Trello**](https://trello.com/)

- Used to time manage the various steps in the project.

[**Balsamiq**](https://balsamiq.com/)

- Balsamiq was used to create wireframes of both the mobile and website before construction began.

[**Gitpod**](https://gitpod.io/)

- I used Gitpod to write my code.

[**Git**](https://git-scm.com/)

- I've used Git version control system to regularly add and commit changes made to project in gitpod thn pushing them to GitHub.

[**Google Fonts**](https://fonts.google.com/)

- I used google fonts to style the text.

[**Bootstrap**](https://getbootstrap.com/docs/4.4/getting-started/introduction/#starter-template)
- I used bootstrap to style my webpage. 

[**HTML**](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)

- HTML is used.

[**CSS**](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS3)

- The project uses CSS to apply style to my site. The style.css is link to the base.html.

[**JavaScript**](https://www.javascript.com/)

- script.js is linked to the base.html file and also written directly into the html file when specific to only that page.

[**jQuery**](https://releases.jquery.com/jquery/)

- I used jQuery for DOM manipulation in my project.

[**Python3**](https://www.python.org/)
- was used to program the join the frontend to the backend. 

[**Flask**](https://flask.palletsprojects.com/en/2.0.x/)

- was used as the micro framework for python3

[**Werkzeug**](https://www.palletsprojects.com/p/werkzeug/)

- Flask wraps Werkzeug, using it to handle the details of WSGI while providing more structure and patterns for defining powerful applications.

[**Jinja**](https://jinja.palletsprojects.com/en/2.11.x/)

- Jinja2 is a full-featured template engine for Python.

[**Heruko**](https://id.heroku.com/login)

- Heruko was used to host and delpoy the site 

[**MongoDB**](https://www.mongodb.com/)
- MongoDB was used as the backend database

[**Radom Key Generator**](https://randomkeygen.com/)
- Ramdom key was used to generate the necessary key to protect the database. 

## Version Control

[**Git**](https://git-scm.com/)

- Git was used to regularly commit changes made to my project.

[**GitHub**](https://github.com/)

- Is used as my Repository.



## Acknowledgements

A special thanks to my mentor Spencer Barriball for his guidance in the project. I also need to thank my partner Chrissy and my Daughter Abbey-Rae for allowing me a great many hours in front of the computer.

### Disclaimer

This is an education only project.
