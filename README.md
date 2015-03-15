Cale Bickler
3/14/2015
DNN Facebook integration project

Using the module

When first viewing the page it will present a Facebook log in button. Click this button and log in to Facebook 
and give permission to the site to access your profile data. Once logged in the button will disappear and a list 
of data about the profile including profile data and likes will display. Below these fields a text area and a button 
will allow the user to enter a status update from the page.

Installing the Module in DNN

Download zipped file.
Create new DNN platform site (if one is not already created).
Use Nuget to install Bootstrap
Log in to the DNN Admin account.
Click on Host dropdown at the top and click Extenstions.
Click on Install Extension Wizard and choose the zipped file.
Click next until created.
Now click on Modules dropdown and select Add New Module.
Select Cale Bickler and drag the Facebook Integration module to the page.
Exit edit mode and refresh the page.
Now you will need to use a Facebook app that is using the current URL.
Create or modify a Facebook application and replace the App ID on line 47 of _View.cshtml.
Now the module should work.

Helpful Resources

API Explorer: https://developers.facebook.com/tools-and-support/
Authentication Script:  https://developers.facebook.com/docs/facebook-login/login-flow-for-web/v2.2

Implementation Steps

Downloaded web platform installer and installed DNN Platform, which also included SQL Server 2008.

Created new website with default template.

Added a new page, and added custom module – selected razor view.

Now I see a view page where I can edit the HTML

Created a test element to see what would happen and it displayed on the site.

Next I searched online for DNN Facebook integration and found this: 
http://www.dnnsoftware.com/community-blog/cid/132142/integrating-facebook-comments-into-your-dotnetnuke-pages

I copied the HTML from the site into my view and a Facebook comment section appeared.

Next I looked at the Facebook developer docs. I know we need to display information about the users 
account using the graph feature so I started there.

I copied a JS get request off of the FB developer site and pasted it into my javascript.

Now I get the error an active access token must be used to query, I search Google for how to authenticate 
with Facebook and found https://developers.facebook.com/docs/facebook-login/login-flow-for-web/v2.2  This 
page was very helpful as it game me some javascript that could be used.

Now I can receive my name from Facebook

Now I try to call the node me/local but get an authentication error

Try using the Facebook graph explorer and realize that the permissions checked at the top correspond to the 
data the API calls can retrieve

Now by adding the permission user_about_me when I use the API in my code and call me I get a lot of 
information about my Facebook account.

Spent a while trying to figure out what is the public data for an account but figured out it just comes 
over with the API call /me depending on what authentication permissions you have

The calls to the different nodes needed are: /me,  me/notes and me/likes

That is all the data required but notes says it is deprecated.

Next I lookup how to post to feed, I find that you can use a facebook dialog. But I want to create my own 
textarea and button.

Find through Facebook developer and API explorer the me/feed with the publish_actions permission and that 
works.

Create the text area and button and wire up the click event of the button to post the value of the text 
area to the Facebook API

Both the posts and the gets are working so now I style the page. I try to get bootstrap running on my view. 
I thought it came with DNN preinstalled but it wasn’t working on my view. So I install it with Nuget, 
include the style sheet in my view and now it works.

I create the HTML elements to hold the data, and create functions in the API calls that go through the 
JSON objects and display the values in the appropriate divs.

I also hide the log in button if the user is already authenticated and hide the data displays if they are not.

I also create an error section where I can put any error messages the API calls encounter into.

Do final testing and everything looks good.
