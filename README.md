                                               DJANGO Project
Project Overview:
To  create/update/delete products list in admin console page itself using DJango rest framework.
All new users are authenicated by tokens and customizing the user tables for username as email.
To track all logs inside Djangoprojects by middleware.
To take backup once product saved by signals.
Serialize the models and customize the admin page lookup.

User table Customization[accounts/model]:

Inherited tables from BaseUserManager and AbstractUser, PermissionsMixin to customize the table
By default user as username, here we are changin to email so that we can share info to their mails.
Once user created token generated automatically to user, we can use this token key for authnetication.

Why Token authnetication required?
We neeed to restrict everyone can access all URLs, to achieve this via token we can allow only limited users.

Admin Page Customization[accounts/admin.py]:

We are changing list display default to our own models and applying filter for staffs.
Allow admin user to create with email+password

Table creation[product/models.py] and Serializer[product/serializer.py]:

Three table (produt,orders,product_rating) which was created in model to define table
Creating serializer for all tables inorder to convert JSON response to pythin dictionary viceversa

Forms[product/forms.py]:
To handle user inputs, we need to define forms
Whatever field define in forms, only those field we can handle userinputs


Django Rest Framework[product/drf_views.py]:
Here we tried all three views

Function based view cretaed for orderview view, here added get and post method
so we can get data or post data to tables
Class based view created for order update view, here added get,post,delete method
we are updating order details through this view
Viewset used for product,order,rating view, here all CRED operation came automatically  no need to define seperately

Signals[product/signals]:
Trigger the notification in Django based on action
Once product saved, we taking backup of that product
Backup data stored in fixtures/product.json
Here post save operation used

Middleware[product\middleware.py]:
Middleware act as pipeline between browser and djangoviews
Take request(before reach views)and respond(after view) to them
Whatever action doing inside the project save,delete all action captured as logs stored seperately

Conclusion:
To perform all CRED operation(GET/POST/Delete/PUSH) in browser itself by Django rest framework instead of any external tool(postman).
All backend operation running here for overall orders.





