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
