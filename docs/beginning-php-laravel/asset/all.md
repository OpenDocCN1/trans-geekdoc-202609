 

[About the Author](#part0000.xhtml#_ijxsbioq7syl)

[Introduction](#part0000.xhtml#_9j41n0s56unq)

[Who is this book for](#part0000.xhtml#_57ztu3gkddjb)

[What will you learn](#part0000.xhtml#_3ynjjbi5zzl4)

[Requirements](#part0000.xhtml#_9stfzadyu5rp)

[How the Laravel Framework Works](#part0000.xhtml#_92tfh34gcalh)

[Create a Project](#part0000.xhtml#_48psclxxp5og)

[Templating](#part0000.xhtml#_2b1cjxc2q1xd)

[Defining a Layout](#part0000.xhtml#_94nhdnehxjqj)

[Authentication](#part0000.xhtml#_nzqh8ljsc7r0)

[Login Page](#part0000.xhtml#_35qmxivmnley)

[Registration Page](#part0000.xhtml#_3ujhhg3utsfm)

[Hello Laravel Migrations, Goodbye to Labouring](#part0000.xhtml#_99f3al8l8eem)

[A Little About the .env(DotEnv) File](#part0000.xhtml#_dlln13g4lc7u)

[Login](#part0000.xhtml#_2vcxxpboxws6)

[Building The Dashboard](#part0000.xhtml#_7k8pspvkv9u8)

[SideNav](#part0000.xhtml#_upstc2yob9kr)

[NavBar](#part0000.xhtml#_io8nfu6jdsu1)

[Logout](#part0000.xhtml#_icf6o81xkzoa)

[Displaying A Welcome Message](#part0000.xhtml#_mzlx7i93zoo4)

[Create Inventory](#part0000.xhtml#_27ed8gdl6uup)

[Create an Inventory Model & Define The Relationship](#part0000.xhtml#_z99lwkni335p)

[Defining the Route, Inventory Controller & Request Validation](#part0000.xhtml#_7i9krxbhutry)

[Create Inventory Form & List Inventories](#part0000.xhtml#_wmj5at2eyjas)

[Dependency Injection & Controllers](#part0000.xhtml#_fu6x0g4gotp2)

[The List Inventory View](#part0000.xhtml#_lrfsqwt9l01v)

[Building The Trash Feature](#part0000.xhtml#_rmkud3gwolzj)

[Edit Inventory](#part0000.xhtml#_f5xkfaki3vdb)

[CRON JOB & Task Scheduling](#part0000.xhtml#_4gma68n02qfg)

[Defining a Job](#part0000.xhtml#_ok0hz3jrx8m1)

[Sending Email](#part0000.xhtml#_m61p0b54g66)

[Conclusion](#part0000.xhtml#_rxejb07vw70h)

 

#  

#  

#  

 

 

 

 

 

# About the Author

Oluwafemi Alofe is an experienced software engineer with 7 years of experience building scalable web applications using Laravel, since the early release of version 4.2. He’s currently the Technical Co-Founder (CTO) at a Fintech startup.

#  

#  

#  

#  

 

 

 

 

 

# Introduction

Since its initial release in 2011, Laravel has experienced exponential growth. In 2015, it became the most starred PHP framework on GitHub and rose to the go-to framework for a lot of startups and developers across the globe.

 

Laravel is an MVC framework that focuses on simplicity, clarity, and getting work done. People and companies are using it to build everything from simple hobby projects all the way to Fortune 500 companies.

 

According to [https://hackr.io/](https://hackr.io/) Laravel still remains one of the top ten web development frameworks as of 2019.

 

##  

##  

##  

##  

 

 

 

 

 

 

 

 

 

 

##  

 

 

## Who is this book for

This book is aimed at beginners who are looking to start building applications using Laravel and are ready to get hands-on, pretty fast by building a minimal project that covers most of the Laravel framework basics and a few advanced features that might seem overwhelming to beginners at first. 

 

Intermediate users with some experience, seeking better ways to architect small to medium-sized applications will also find this book beneficial.

 

## What will you learn

This book will show you how to build a simple inventory application. It will cover topics such as Blade Templating where we will be taking a random Bootstrap theme and converting it into a lean template which we can extend for all our pages, Authentication for our registration and login, Eloquent ORM to show you different database table relationships including a feature called soft deletes, Dependency Injection, Email setup and configuration, Routing types, naming and grouping and finally TASK SCHEDULING & CRON JOBS to perform background process.

 

Most of all you will be learning how to write production-quality code by adhering to a standard naming convention, practices and writing DRY(Do, not repeat yourself) codes.

 

The code to this project is hosted and can be found on  GitHub here 

 

 
| https://github.com/slim12kg/Beginning-PHP-Laravel-Ebook-Code.git  |
| --- |

 

 

 

 

 

 

 

��Note

One thing recruiters look out for when searching for a Laravel developer is the number of projects you have completely built, using the framework. So it’s advisable to follow through with this book and not only clone or fork this repo.

 

## Requirements

For the purpose of this book, we would be using Laravel 5.4 because of its support for PHP version >= 5.6.4 which is still mostly used by a lot of people. If you wish, you can go ahead to install a higher version than 5.4 but not lower.

 

 Ensure you have PHP installed on your system with the following extensions enabled

 

●         OpenSSL PHP Extension

●         PDO PHP Extension

●         Mbstring PHP Extension

●         Tokenizer PHP Extension

●         XML PHP Extension

 

Composer (A PHP dependency manager) must be installed globally on your machine and MySql or MariaDB database either packaged with Xammp or directly installed.

 

I will be assuming you are either using a Unix Terminal or Windows Git Bash to run commands.

 

 

 

Resources

●         [How to use GIT BASH to install and run Laravel](https://www.youtube.com/watch?v=0rAW5eah7pw)

●         [Install Laravel on Mac with valet](https://www.youtube.com/watch?v=ErblOwpiopI)

●         [Laravel setup on Ubuntu using Xampp](https://www.youtube.com/watch?v=3DeJCwmlOys)

●         [Setting up Laravel 5.4 for Linux](https://www.youtube.com/watch?v=l-hM9KG4VSE&t=19s)

●         [Official Laravel installation guide](https://laravel.com/docs/5.4/installation)

●         [Install Laravel 5 on windows with Xampp](https://www.codementor.io/@magarrent/how-to-install-laravel-5-xampp-windows-du107u9ji)

 

 

 

 

 

 

 

 

 

��Note

So as not to overwhelm beginners we would not be following the TDD (Test Driven Development) process. To find out more about TDD I [recommend reading this](https://github.com/slim12kg/Learn-Test-Driven-Design-In-Laravel).

# How the Laravel Framework Works

![](Images/image00200.jpeg)

 

 

Image source: https://www.netsolutions.com

 

Laravel is an MVC framework meaning Model, View & Controller. Our Model is used to retrieve and store information in the database, View is what renders in the browser that end-users can see while the Controller is where the business logic of the app is done e.g like manipulating data from the model and passing to the view.

 

 

 

 

 

 

 

 

 

 

 

 

 

 

��Note

For a deeper understanding, you can read https://laravel.com/docs/5.8/lifecycle  about the Laravel request Lifecycle.

# Create a Project

Open a new terminal or command line (gitbash for window OS users), navigate to your web projects directory and run the below command to create a new Laravel project. Ensure Composer is installed globally on your machine.

 

 
| composer create-project --prefer-dist laravel/laravel inventory-app "5.4.\*"  |
| --- |

 

Next, create a database called inventory\_app and give all privileged access to the root user or a preferred user you choose to allow all access to this database. 

 

Once the Composer command is done running and has completely installed your new Laravel project without throwing errors. From your terminal, navigate to the newly created inventory-app directory, then run command php artisan serve to launch your project to be accessed via your web browser.

 

This is me running the php artisan serve command from the inventory app project directory from my terminal.

 

 
| oluwafemialofe@Oluwafemis-MacBook-Air inventory-app : php artisan serve |
| --- |

 

You will get an output like below, simply open your browser and visit the outputted URL

 

 
| Laravel development server started: <http://127.0.0.1:8000> |
| --- |

 

You should now be presented with the Laravel default landing page. 

 

Congratulations, you are on your way to becoming a Laravel Artisan ⚔

#  

 

 

 

 

 

 

 

# Templating

We are going to use StartBootstrap Simple Sidebar Theme, one of the free bootstrap 4 basic templates available freely online to create our view scaffold. You can find it here [https://blackrockdigital.github.io/startbootstrap-simple-sidebar](https://blackrockdigital.github.io/startbootstrap-simple-sidebar/), right-click on the page and click the view page source to copy the HTML code.

 

 

 
| <!DOCTYPE html>  
<html lang="en"\>  
  
<head\>  
  
  <meta charset="utf-8"\>  
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no"\>  
  <meta name="description" content=""\>  
  <meta name="author" content=""\>  
  
  <title\>Simple Sidebar - Start Bootstrap Template</title\>  
  
  <!-- Bootstrap core CSS -->  
  <link href="vendor/bootstrap/css/bootstrap.min.css" rel="stylesheet"\>  
  
  <!-- Custom styles for this template -->  
  <link href="css/simple-sidebar.css" rel="stylesheet"\>  
  
</head\>  
  
<body\>  
  
  <div class="d-flex" id="wrapper"\>  
  
    <!-- Sidebar -->  
    <div class="bg-light border-right" id="sidebar-wrapper"\>  
      <div class="sidebar-heading"\>Start Bootstrap </div\>  
      <div class="list-group list-group-flush"\>  
        <a href="#" class="list-group-item list-group-item-action bg-light"\>Dashboard</a\>  
        <a href="#" class="list-group-item list-group-item-action bg-light"\>Shortcuts</a\>  
        <a href="#" class="list-group-item list-group-item-action bg-light"\>Overview</a\>  
        <a href="#" class="list-group-item list-group-item-action bg-light"\>Events</a\>  
        <a href="#" class="list-group-item list-group-item-action bg-light"\>Profile</a\>  
        <a href="#" class="list-group-item list-group-item-action bg-light"\>Status</a\>  
      </div\>  
    </div\>  
    <!-- /#sidebar-wrapper -->  
  
    <!-- Page Content -->  
    <div id="page-content-wrapper"\>  
  
      <nav class="navbar navbar-expand-lg navbar-light bg-light border-bottom"\>  
        <button class="btn btn-primary" id="menu-toggle"\>Toggle Menu</button\>  
  
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation"\>  
          <span class="navbar-toggler-icon"\></span\>  
        </button\>  
  
        <div class="collapse navbar-collapse" id="navbarSupportedContent"\>  
          <ul class="navbar-nav ml-auto mt-2 mt-lg-0"\>  
            <li class="nav-item active"\>  
              <a class="nav-link" href="#"\>Home <span class="sr-only"\>(current)</span\></a\>  
            </li\>  
            <li class="nav-item"\>  
              <a class="nav-link" href="#"\>Link</a\>  
            </li\>  
            <li class="nav-item dropdown"\>  
              <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"\>  
                Dropdown  
              </a\>  
              <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdown"\>  
                <a class="dropdown-item" href="#"\>Action</a\>  
                <a class="dropdown-item" href="#"\>Another action</a\>  
                <div class="dropdown-divider"\></div\>  
                <a class="dropdown-item" href="#"\>Something else here</a\>  
              </div\>  
            </li\>  
          </ul\>  
        </div\>  
      </nav\>  
  
      <div class="container-fluid"\>  
        <h1 class="mt-4"\>Simple Sidebar</h1\>  
        <p\>The starting state of the menu will appear collapsed on smaller screens, and will appear non-collapsed on larger screens. When toggled using the button below, the menu will change.</p\>  
        <p\>Make sure to keep all page content within the <code\>#page-content-wrapper</code\>. The top navbar is optional, and just for demonstration. Just create an element with the <code\>#menu-toggle</code\> ID which will toggle the menu when clicked.</p\>  
      </div\>  
    </div\>  
    <!-- /#page-content-wrapper -->  
  
  </div\>  
  <!-- /#wrapper -->  
  
  <!-- Bootstrap core JavaScript -->  
  <script src="vendor/jquery/jquery.min.js"\></script\>  
  <script src="vendor/bootstrap/js/bootstrap.bundle.min.js"\></script\>  
  <!-- Menu Toggle Script -->  
  <script\>  
    $("#menu-toggle").click(function(e) {  
      e.preventDefault();  
      $("#wrapper").toggleClass("toggled");  
    });  
  </script\>  
  
</body\>  
  
</html\> |
| --- |

Open the inventory project in your preferred editor, I use PHPStorm.  Navigate to resources > welcome.blade.php and replace the content with the source code of the bootstrap theme above.

 

Notice if you reload the app in your browser it will show without style which looks very terrible, now head on to the official bootstrap website to download bootstrap 4.3, the compiled version. 

 

You can directly copy and paste the link below into your browser to download it.

 

 
| https://github.com/twbs/bootstrap/releases/download/v4.3.1/bootstrap-4.3.1-dist.zip |
| --- |

 

Extract the zip files, locate bootstrap.min.css file, copy it to your project directory under public/css, locate bootstrap.bundle.min.js file and copy it to  public/js. Bootstrap needs jquery support, so create a new file jquery.min.js under public/js and visit the url below in your browser and copy the content inside the file.

 

 
| https://code.jquery.com/jquery-3.4.1.min.js |
| --- |

 

Now we need to reference the new bootstrap and jquery assets we just added to our project on the welcome.blade.php page. In order to do so, replace the old reference with a new one.

 

 

 
| //Replace this  
<script src="vendor/jquery/jquery.min.js"\></script>  
<script src="vendor/bootstrap/js/bootstrap.bundle.min.js"\></script>  
  
//With this  
<script src="{{asset('js/jquery.min.js')}}"\></script>  
<script src="{{asset('js/bootstrap.bundle.min.js')}}"\></script> |
| --- |

 

 

 
| //Replace this  
<link href="vendor/bootstrap/css/bootstrap.min.css" rel="stylesheet"\>  
  
//With this  
<link href="{{asset('css/bootstrap.min.css')}}" rel="stylesheet"\> |
| --- |

 

Now create a new file simple-sidebar.css under the public/css folder and paste the below content inside the file.

 

 
| body {  
  overflow-x: hidden;  
}  
  
#sidebar-wrapper {  
  min-height: 100vh;  
  margin-left: -15rem;  
  \-webkit-transition: margin .25s ease-out;  
  \-moz-transition: margin .25s ease-out;  
  \-o-transition: margin .25s ease-out;  
  transition: margin .25s ease-out;  
}  
  
#sidebar-wrapper .sidebar-heading {  
  padding: 0.875rem 1.25rem;  
  font-size: 1.2rem;  
}  
  
#sidebar-wrapper .list-group {  
  width: 15rem;  
}  
  
#page-content-wrapper {  
  min-width: 100vw;  
}  
  
#wrapper.toggled #sidebar-wrapper {  
  margin-left: 0;  
}  
  
@media (min-width: 768px) {  
  #sidebar-wrapper {  
    margin-left: 0;  
  }  
  #page-content-wrapper {  
    min-width: 0;  
    width: 100%;  
  }  
  #wrapper.toggled #sidebar-wrapper {  
    margin-left: -15rem;  
  }  
} |
| --- |

 

Change the old reference of the sidebar css to the new one we just created.

 

 
| //Replace this  
 <link href="css/simple-sidebar.css" rel="stylesheet"\>  
  
//With this  
<link href="{{asset('css/simple-sidebar.css')}}" rel="stylesheet"\> |
| --- |

 

The welcome page should load fine now.

## Defining a Layout

Since we would be maintaining a similar view across pages, Laravel provides us with a way to define a master layout where other pages, known as child view can extend from. So things such as navigation, header styles, footer script or content can remain in a master view where child view extending it can extend and override some part of it, depending on how we define it and what we want.

 

Create a layout folder in resources/views and create a file called master.blade.php then inside this file paste the content of  resources/views/welcome.blade.php. After pasting in the content, now I want you to take out the content from the opening and closing header tags, that is between <head> to </head> then create a partials folder under the layout directory, create a \_header.blade.php file inside the partials folder and paste the content we took out between the head tags from the master.blade.php inside \_header.blade.php.

 

 
| // resources/views/layout/partials/\_header.blade.php  
  
<head\>  
    <meta charset="utf-8"\>  
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no"\>  
    <meta name="description" content=""\>  
    <meta name="author" content=""\>  
    <title\>Simple Sidebar - Start Bootstrap Template</title\>  
    <link href="{{asset('css/bootstrap.min.css')}}" rel="stylesheet"\>  
      <link href="{{asset('css/simple-sidebar.css')}}" rel="stylesheet"\>  
</head\> |
| --- |

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

��Note

Laravel uses the  Blade templating engine. Unlike other popular PHP templating engines, Blade does not restrict you from using plain PHP code in your views. In fact, all Blade views are compiled into plain PHP code and cached until they are modified, meaning Blade adds essentially zero overhead to your application. Blade view files use the .blade.php file extension and are typically stored in the resources/views directory.

 

Notice the addition of underscore before the header file name, this is to mark that this view is a partial file and can’t stand on its own. Next take out all the script tags near the body close tag </body>, create a new file \_footer.blade.php and paste what you took out inside of it.  

 
| // resources/views/layout/partials/\_footer.blade.php  
  
<!-- Bootstrap core JavaScript -->  
<script src="{{asset('js/jquery.min.js')}}"\></script\>  
<script src="{{asset('js/bootstrap.bundle.min.js')}}"\></script\>  
<!-- Menu Toggle Script -->  
<script\>  
    $("#menu-toggle").click(function(e) {  
        e.preventDefault();  
        $("#wrapper").toggleClass("toggled");  
    });  
</script\> |
| --- |

 

Next take out the content between the Sidebar comments from the master view, create a new file called \_sidebar.blade.php and place inside the content you took out.

 

 
| // resources/views/layout/partials/\_sidenav.blade.php  
  
<!-- Sidebar -->  
    <div class="bg-light border-right" id="sidebar-wrapper"\>  
        <div class="sidebar-heading"\>Start Bootstrap </div\>  
        <div class="list-group list-group-flush"\>  
            <a href="#" class="list-group-item list-group-item-action bg-light"\>Dashboard</a\>  
            <a href="#" class="list-group-item list-group-item-action bg-light"\>Shortcuts</a\>  
            <a href="#" class="list-group-item list-group-item-action bg-light"\>Overview</a\>  
            <a href="#" class="list-group-item list-group-item-action bg-light"\>Events</a\>  
            <a href="#" class="list-group-item list-group-item-action bg-light"\>Profile</a\>  
            <a href="#" class="list-group-item list-group-item-action bg-light"\>Status</a\>  
        </div\>  
    </div\><!-- /#sidebar-wrapper --> |
| --- |

 

Again take out the navbar inside the div with id page-content-wrapper, create a new file \_navbar.blade.php and place inside the content you took out, now your file should look like below.

 

 
| // resources/views/layout/partials/\_navbar.blade.php  
  
<nav class="navbar navbar-expand-lg navbar-light bg-light border-bottom"\>  
    <button class="btn btn-primary" id="menu-toggle"\>Toggle Menu</button\>  
  
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation"\>  
        <span class="navbar-toggler-icon"\></span\>  
    </button\>  
  
    <div class="collapse navbar-collapse" id="navbarSupportedContent"\>  
        <ul class="navbar-nav ml-auto mt-2 mt-lg-0"\>  
            <li class="nav-item active"\>  
                <a class="nav-link" href="#"\>Home <span class="sr-only"\>(current)</span\></a\>  
            </li\>  
            <li class="nav-item"\>  
                <a class="nav-link" href="#"\>Link</a\>  
            </li\>  
            <li class="nav-item dropdown"\>  
                <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"\>  
                    Dropdown  
                </a\>  
                <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdown"\>  
                    <a class="dropdown-item" href="#"\>Action</a\>  
                    <a class="dropdown-item" href="#"\>Another action</a\>  
                    <div class="dropdown-divider"\></div\>  
                    <a class="dropdown-item" href="#"\>Something else here</a\>  
                </div\>  
            </li\>  
        </ul\>  
    </div\>  
</nav\> |
| --- |

 

Replace all the sections you took out, with the references to the new files you created and moved the content to, using the blade template @include directive which is similar to the php include function.

 

 
| //Replace where we took out the header tag with this  
@include('layout.partials.\_header')  
  
//Replace where we took out the side nav with this  
@section('sidenav')  
    @include('layout.partials.\_sidenav')  
@show  
 //Replace where we took out the navbar with this  
@section('navbar')  
    @include('layout.partials.\_navbar')  
@show  
  
//Replace where we took out the script tags with this  
@include('layout.partials.\_footer') |
| --- |

 

 

 

 

 

 

 

 

 

 

��Note

@section directives allows us to define sections we can override in individual child views, when we do. 

 

 

Now replace the content of welcome.blade.php with code below, I will explain shortly.

 

 
| @extends('layout.master')  
  
@section('content')  
  
    //Content specific to this child page will appear here  
  
@endsection |
| --- |

 

Take out the whole content inside the div with the class container-fluid from the master template and paste it in between the content section of the welcome.blade.php page, then replace where you took out the div content with @yield(‘content’). Our master.blade.php should now look like below.

 

 
| // resources/views/layout/master.blade.php  
  
<!DOCTYPE html>  
<html lang="en"\>  
@include('layout.partials.\_header')  
<body\>  
<div class="d-flex" id="wrapper"\>  
    @section('sidenav')  
        @include('layout.partials.\_sidenav')  
    @show  
    <div id="page-content-wrapper"\>  
        @section('navbar')  
            @include('layout.partials.\_navbar')  
        @show  
          
        @yield('content')  
    </div\>  
</div\>  
@include('layout.partials.\_footer')  
</body\>  
</html\> |
| --- |

 

 

 

 

Notice the use of @yield(‘content’) directive, the content parameter inside the @yield directive, you can name it any other thing you want, not necessarily content, e.g child-page,  but in our case content is fine and will be for most cases, since it's just a parameter to reference a section to be placed within a child view. Notice the welcome page, you will see the use of the section there and in between the section we place the content unique to the view which substitute the @yield directive in the master view it extends.

 

We can also use a @yield directive inside the head tag, to define page title for each child view.

 

 
| //Replace this  
<title\>Simple Sidebar - Start Bootstrap Template</title\>  
  
//With this  
<title\> Inventory App -  @yield('page-title') </title\> |
| --- |

 

Our welcome.blade.php view should look like below.

 

 
| @extends('layout.master')  
  
@section('page-title')  
    Welcome  
@endsection  
  
@section('content')  
    <div class="container-fluid"\>  
        <h1 class="mt-4"\>Simple Sidebar</h1\>  
        <p\>The starting state of the menu will appear collapsed on smaller screens, and will appear non-collapsed on larger screens. When toggled using the button below, the menu will change.</p\>  
        <p\>Make sure to keep all page content within the <code\>#page-content-wrapper</code\>. The top navbar is optional, and just for demonstration. Just create an element with the <code\>#menu-toggle</code\> ID which will toggle the menu when clicked.</p\>  
    </div\>  
@endsection |
| --- |

 

Now reload your page in the browser, everything should load fine with the page title changed to Welcome in the browser tab.

 

Play around with the layouts, try to make the master.blade.php leaner than it currently is or define a yield directive to insert additional styles to the head tag or scripts in the footer tag.

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

# Authentication 

In this chapter we will be building the registration and login system for our Inventory App. Laravel already ships with everything out of the box for you, you don’t have to maintain sessions, you can always configure the Laravel auth at config/auth.php.

 

Using the artisan command-line interface, Laravel allows us to generate an authentication scaffold by running in your terminal or git bash from the inventory project directory root.

 

 
| php artisan make:auth |
| --- |

 

Once you run the command successfully you will get a message that says Authentication scaffolding generated successfully, to confirm this visit http://127.0.0.1:8000/login and http://127.0.0.1:8000/register you will notice that a usable login page and registration page was auto generated for us, isn’t that lovely?

 

From your editor, under the views/auth directory you will notice the new blade files for registration, login and forgot password, also under Http/Controllers you will see a new HomeController.php class generated.

 

 

 

 

 

 

 

 

 

 

 

 

 

 

��Note

Artisan is the command-line interface included with Laravel. It provides a number of helpful commands that can assist you while you build your application. To view a list of all available Artisan commands, you may use the list command: 

 

 
| php artisan list |
| --- |

## Login Page

Let us edit our login page to extend our own master template. For the login view, we don’t need the sidenav, navbar and we need the login form centered in the middle of the page. Here is how the login page code turns out.

 

 
| // resources/views/auth/login.blade.php  
  
@extends('layout.master')  
  
@section('sidenav')  
    {{--//--}}  
@endsection  
  
@section('navbar')  
    {{--//--}}  
@endsection  
  
@section('content')  
        <div class\="row">  
            <div class\="col\-md\-4 mx\-auto mt\-5 border">  
                <div class\="panel panel\-default">  
                    <div class\="panel\-heading text\-center pt\-4">  
                        <h4\>Login</h4\>  
                    </div\>  
                    <div class\="panel\-body">  
                        <form class\="form\-horizontal" method\="POST" action\="{{ route('login') }}">  
                            {{ csrf\_field() }}  
  
                            <div class="form-group{{ $errors->has('email') ? ' has-error' : '' }}">  
                                <label for="email" class="col-md\-4 control-label">E-Mail Address</label>  
  
                                <div class="col-md\-12">  
                                    <input id="email" type="email" class="form-control" name="email" value="{{ old('email') }}" required autofocus>  
  
                                    @if ($errors->has('email'))  
                                        <span class="help-block">  
                                        <strong>{{ $errors->first('email') }}</strong>  
                                    </span>  
                                    @endif  
                                </div>  
                            </div>  
  
                            <div class="form-group{{ $errors->has('password') ? ' has-error' : '' }}">  
                                <label for="password" class="col-md\-4 control-label">Password</label>  
  
                                <div class="col-md\-12">  
                                    <input id="password" type="password" class="form-control" name="password" required>  
  
                                    @if ($errors->has('password'))  
                                        <span class="help-block">  
                                        <strong>{{ $errors->first('password') }}</strong>  
                                    </span>  
                                    @endif  
                                </div>  
                            </div>  
  
                            <div class="form-group">  
                                <div class="ml\-3">  
                                    <div class="checkbox">  
                                        <label>  
                                            <input type="checkbox" name="remember" {{ old('remember') ? 'checked' : '' }}> Remember Me  
                                        </label>  
                                    </div>  
                                </div>  
                            </div>  
  
                            <div class="form-group">                                <div class="col-md-12">                                    <button type="submit" class="btn btn-primary">                                        Login                                    </button>                                     <a class="btn btn-link d-inline" href="{{ route('register') }}">                                        Register                                    </a>|                                    <a class="btn btn-link d-inline" href="{{ route('password.request') }}">                                        Forgot Your Password?                                    </a>                                </div>                            </div>                        </form>  
                    </div>  
                </div>  
            </div>  
        </div>  
@endsection |
| --- |

 

Copy the above code and paste in your resources/views/auth/login.blade.php file, save and refresh your login page. You should see the difference not! It looks better isn’t it?

 

Notice the way we added an empty comment between the sidebar and navbar sections to override it and not show any content on both parts on the login page. 

 

Like this

 

 
| @section('sidenav')  
    {{--//--}}  
@endsection  
  
@section('navbar')  
    {{--//--}}  
@endsection |
| --- |

##  

 

## Registration Page

Let us also edit the register page to extend our own master layout and not the auto generated scaffold layout.

 

For our registration page, we would be using additional css to slightly position the anchor tag that links back to our login page up. A neater way to do this is add a @yield tag to our master layout to inject a css section from any child page if required. So just before the closing body tag on the master blade layout blade template add this.

 

 
| @yield('styles') |
| --- |

 

Registration page complete code will look like below.

 

 
| @extends('layout.master')  
  
@section('sidenav')  
    {{--//--}}  
@endsection  
  
@section('navbar')  
    {{--//--}}  
@endsection  
  
@section('content')  
    <div class\="row">  
        <div class\="col\-md\-4 mx\-auto mt\-5 border">  
            <div class\="panel panel\-default">  
                <div class\="panel\-heading text\-center pt\-4">  
                    <h4\>Register</h4\>  
                </div\>  
                <div class\="panel\-body">  
                    <form class\="form\-horizontal" method\="POST" action\="{{ route('register') }}">  
                        {{ csrf\_field() }}  
  
                        <div class="form-group{{ $errors->has('name') ? ' has-error' : '' }}">  
                            <label for="name" class="col-md\-12 control-label">Name</label>  
  
                            <div class="col-md\-12">  
                                <input id="name" type="text" class="form-control" name="name" value="{{ old('name') }}" required autofocus>  
  
                                @if ($errors->has('name'))  
                                    <span class="help-block">  
                                        <strong>{{ $errors->first('name') }}</strong>  
                                    </span>  
                                @endif  
                            </div>  
                        </div>  
  
                        <div class="form-group{{ $errors->has('email') ? ' has-error' : '' }}">  
                            <label for="email" class="col-md\-4 control-label">E-Mail Address</label>  
  
                            <div class="col-md\-12">  
                                <input id="email" type="email" class="form-control" name="email" value="{{ old('email') }}" required>  
  
                                @if ($errors->has('email'))  
                                    <span class="help-block">  
                                        <strong>{{ $errors->first('email') }}</strong>  
                                    </span>  
                                @endif  
                            </div>  
                        </div>  
  
                        <div class="form-group{{ $errors->has('password') ? ' has-error' : '' }}">  
                            <label for="password" class="col-md\-4 control-label">Password</label>  
  
                            <div class="col-md\-12">  
                                <input id="password" type="password" class="form-control" name="password" required>  
  
                                @if ($errors->has('password'))  
                                    <span class="help-block">  
                                        <strong>{{ $errors->first('password') }}</strong>  
                                    </span>  
                                @endif  
                            </div>  
                        </div>  
  
                        <div class="form-group">  
                            <label for="password-confirm" class="col-md\-12 control-label">Confirm Password</label>  
  
                            <div class="col-md\-12">  
                                <input id="password-confirm" type="password" class="form-control" name="password\_confirmation" required>  
                            </div>  
                        </div>  
  
                        <div class="form-group">  
                            <div class="col-md\-12 col-md-offset\-4">  
                                <button type="submit" class="btn btn-primary">  
                                    Register  
                                </button>  
                                <span class="ml\-3">Already have an account?</span>  
                                <a id="login" class="btn btn-link d-inline pl\-0" href="{{ route('login') }}">  
                                    Login  
                                </a>  
                            </div>  
                        </div>  
                    </form>  
                </div>  
            </div>  
        </div>  
    </div>  
@endsection  
  
@section('styles')  
    <style type="text/css">  
        #login{  
            position: relative;  
            bottom: 2.5px;  
        }  
    </style>  
@endsection |
| --- |

 

Now, we need to setup our app routes, located at routes/web.php and create a controller called AppController.php. From your terminal or git bash run

 

 
| php artisan make:controller AppController |
| --- |

 

A class of AppController will be generated in the app/Http/Controllers directory. Laravel allows you define a route (url basically) for a controller which in return renders a view or returns data, which maybe either be fetched from the database or not, manipulated or not and in return passed  to a view(.blade files) to be rendered or JSON data as an end point.  This will all be clear to you shortly.

 

Locate routes/web.php where Laravel allows us to define web routes then override the whole content with the code below.

 

 
| <?php  
  
Auth::routes();  
  
Route::get('/', function () {  
    return redirect()->route('inventory.home');  
});  
  
Route::group(\['prefix' => 'app','middleware' => 'auth'\],function($route){  
    $route->get('/', 'AppController@dashboard')->name('inventory.home');  
}); |
| --- |

 

What we did here is to define a group route. Laravel allows us to define a group route so we can apply the same url prefix , middleware and a few other options to all routes in that group. In our case we applied a prefix of app and a middleware of auth.  All URL in this group starts with /app prefix and the middleware auth prevent any user not logged to not be able to access all route in this group, also notice the name function that allows us give an alias name which can defined to be  easily memorizable,, in our case we named the route that renders our dashboard  inventory.home  and referenced it in a redirect when a user visits the / route from their browser.

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

��Note

Middleware provides a convenient mechanism for filtering HTTP requests entering your application. Laravel auth middleware verifies the user of your application is login. If the user is not, the user will be redirected to the login screen. However, if the user is logged in, the middleware will allow the request to proceed further into the application.There are [several middlewares](https://laravel.com/docs/5.8/middleware) already shipped with Laravel or you can create additional middleware yourself.

 

Laravel allows you define routes based on the requests type, there are the get, post, put, delete and any request methods. To view a page, the get route is applicable, to submit a form the post route is applicable, to update a form the put route is applicable and likewise for dropping a row in the database the delete route is. If you are new to this it might look very strange but in actual fact this are just http verbs.

 

Using our /app url definitions as a case study, we defined a get  request type. When users visit the url the method dashboard in AppController is called.

 

 
| $route->get('/', 'AppController@dashboard')->name('inventory.home'); |
| --- |

 

Another case study is a basic form of defining Laravel route, by passing a Closure that can return a response in the form of a view, data or redirect. In our case we returned a redirect to our app dashboard.

 

 
| Route::get('/', function () {  
    return redirect()->route('inventory.home');  
}); |
| --- |

 

Next open the AppController and add the method dashboard inside the AppController Class.

 

 
| public function dashboard()  
{  
    return view('dashboard');  
} |
| --- |

 

Now if you visit http://127.0.0.1: 8000/app you will be redirected back to login if you are not authenticated, now that the route to our dashboard is protected with the auth middleware.

 

Open this two files, Http/Controllers/Auth/LoginController.php and Http/Controllers/Auth/RegisterController.php  in your editor and change the redirect url property from /home to /app since there is no /home route defined again.

 

Your files should be updated to look like below

 

 
| protected $redirectTo = '/app'; |
| --- |

 

## Hello Laravel Migrations, Goodbye to Labouring

Have you ever had to deal with creating databases with a lot of tables having many columns? Only for you to change the schema one time or the other? How easy has it been trying to collaborate on a project and there is no easy way to know what schema already exist or what relationship or constraint is defined and have an easy way for everyone to keep the same version of schema without having to tell them what to add or what not, having to labour! Laravel migrations to the rescue!

 

As defined by Laravel documentation migrations are like version control for your database, allowing your team to easily modify and share the application's database schema. Migrations are typically paired with Laravel's schema builder to easily build your application's database schema. If you have ever had to tell a teammate to manually add a column to their local database schema, you've faced the problem that database migrations solve.

 

We would be creating migrations later, but for now we will be running the existing user and password migrations. To create a new migration we need to run command

 

 
| php artisan make:migration create\_{table name in plural}\_table  
  
// e.g  
php artisan make:migration create\_users\_table |
| --- |

 

To run existing migrations, after defining the columns, simply run

 
| php artisan migrate  |
| --- |

 

Or to drop(rollback) the last table 

 
| php artisan migrate:rollback |
| --- |

 

Or to rollback all tables in a database and create them back immediately to clear the existing data run.

 

 
| php artisan migrate:reset |
| --- |

 

 

There are a lot of things to Laravel migrations, that is beyond the scope of this book but nevertheless we would be covering most of the important aspects to it . Visit Laravel official documentation https://laravel.com/docs/5.8/migrations to learn more.

 

To migrate our existing user migration, already shipped with your Laravel installation under database/migrations directory. We need to first create a database called inventory\_app using any of your most preferred database manager, could be using mysql via command line, phpmyadmin, sequelpro or whatever, next create a .env file in your inventory\_app project root directory from your editor and copy the content from already existing .env.example into it.

 

Finally edit the .env file and change the value of the database connection to yours.

 

 
| DB\_CONNECTION=mysql  
DB\_HOST=127.0.0.1  
DB\_PORT=3306  
DB\_DATABASE=inventory\_app  
DB\_USERNAME=root  
DB\_PASSWORD=mypassword |
| --- |

 

 

 Now run

 

 
| php artisan:migrate |
| --- |

 

From your terminal or git bash. If you are getting an error Syntax error or access violation: 1231 Variable 'sql\_mode' can't be set to the value of 'NO\_AUTO\_CREATE\_USER' , simply locate the file config/database.php from your editor, and on line 55 after engine=> null, paste this snippet of code, then rerun your migration.

 

 
| 'modes'  => \[  
                'ONLY\_FULL\_GROUP\_BY',  
                'STRICT\_TRANS\_TABLES',  
                'NO\_ZERO\_IN\_DATE',  
                'NO\_ZERO\_DATE',  
                'ERROR\_FOR\_DIVISION\_BY\_ZERO',  
                'NO\_ENGINE\_SUBSTITUTION',            \], |
| --- |

 

 

## A Little About the .env(DotEnv) File

 

env file which contains environment variables for your app settings, it contains a one row – one KEY=VALUE pair. And within your Laravel project code you can get those environment variables with function env('KEY').

 

Laravel's .env file is included to use, so it's easy to have a different configuration based on the environment your app is running on. This gives you the flexibility to have different variables for local, staging, production, and even different developers' machines.

 

Your .env file should not be committed to your application's source control (e.g git), since each developer/server using your application could require a different environment configuration. Furthermore, this would be a security risk in the event an intruder gains access to your source control repository, since any sensitive credentials would get exposed.

 

Rule of thumb, always add your .env to .gitignore if you use git for your version control, so your credentials do not get pushed to public eyes.

 

 

 

## Login

 

Before we proceed it's important to know that once you update your .env file, you have to reserve your Laravel application, this is because everytime you serve a Laravel application the environment variable is loaded and you would have to restart it to load the new changes.

 

Stop the current php artisan serve command running on the terminal and run the command again. Visit the registration page http://127.0.0.1:8000/register to create an account and you will be automatically logged in to the app dashboard.

 

 

 

 

 

 

 

# Building The Dashboard

In this chapter we would start by restructuring the view of our dashboard, topbar and sidenav, then move on to implement each of the sidenav features.

 

Here are the list of features we would be building

 

●         Show a welcome message to logged in users and the number of inventories available.

●         Create inventory.

●         List all inventories.

●         Edit inventory if it was created by a logged in user.

●         Delete inventory if it was created by a logged in user.

●         Trash listing deleted inventory and how long left before clearing from trash.

●         Cron job to clear expired inventory from trash 3mins after in trash.

## SideNav

Change the placeholder sidenav content from our borrowed bootstrap theme.  Edit your resources/views/layout/partials/\_sidenav.blade.php to match below.

 

 
| <div class\="bg\-light border\-right" id\="sidebar\-wrapper">  
    <div class\="sidebar\-heading">{{config('app.name')}}</div>  
    <div class\="list\-group list\-group\-flush">  
        <a href\="#" class\="list\-group\-item list\-group\-item\-action bg\-light">Dashboard</a\>  
        <a href\="#" class\="list\-group\-item list\-group\-item\-action bg\-light">View Inventories</a\>  
        <a href\="#" class\="list\-group\-item list\-group\-item\-action bg\-light">New Inventory</a\>  
        <a href\="#" class\="list\-group\-item list\-group\-item\-action bg\-light">Trash</a\>  
        <a href\="#" class\="list\-group\-item list\-group\-item\-action bg\-light">Logout</a\>  
    </div\>  
</div\> |
| --- |

 

 

Notice the use of config function to get the app name defined in the .env file. We will be updating the APP\_NAME key to the value Laraventory in the .env file. Now re-serve the application by stopping the current  php artisan serve command and rerunning it from the terminal, so the server can load the new changes made.

 

��Note

In blade templating {{ config(‘app.name’)}} is the same as <?php echo config(‘app.name’) ?> and <?php if( a == b) {  echo ‘True’ }else{ echo ‘False’ } is also same as 

@if(a === b) {{‘True’}} @else {{‘False’}}. 

 

More on using blade templating https://laravel.com/docs/5.4/blade#displaying-data here.

## NavBar 

Change the placeholder navbar content from our borrowed bootstrap theme.  Edit your resources/views/layout/partials/\_navbar.blade.php to match below. 

 

 
| <nav class\="navbar navbar\-expand\-lg navbar\-light bg\-light border\-bottom">  
    <button class\="btn btn\-primary" id\="menu\-toggle">☰</button\>  
  
    <button class\="navbar\-toggler" type\="button" data\-toggle\="collapse" data\-target\="#navbarSupportedContent" aria\-controls\="navbarSupportedContent" aria\-expanded\="false" aria\-label\="Toggle navigation">  
        <span class\="navbar\-toggler\-icon"></span\>  
    </button\>  
  
    <div class\="collapse navbar\-collapse" id\="navbarSupportedContent">  
        <ul class\="navbar\-nav ml\-auto mt\-2 mt\-lg\-0">  
            <li class\="nav\-item dropdown">  
                <a class\="nav\-link dropdown\-toggle" href\="#" id\="navbarDropdown" role\="button" data\-toggle\="dropdown" aria\-haspopup\="true" aria\-expanded\="false">  
                    Account Settings  
                </a\>  
                <div class\="dropdown\-menu dropdown\-menu\-right" aria\-labelledby\="navbarDropdown">  
                    <a class\="dropdown\-item" href\="#">Edit Profile</a\>  
                    <a class\="dropdown\-item" href\="#">Change Password</a\>  
                    <div class\="dropdown\-divider"></div\>  
                    <a class\="dropdown\-item" href\="{{ route('logout') }}"  
                       onclick="event.preventDefault(); document.getElementById('logout-form').submit();">  
                        Logout  
                        <form id="logout-form" action="{{ route('logout') }}" method="POST" style="display: none;">  
                            {{ csrf\_field() }}  
                        </form>  
                    </a>  
                </div>  
            </li>  
        </ul>  
    </div>  
</nav> |
| --- |

 

 

Now if you refresh your page, it's starting to look like a real Laraventory app, click on the account settings menu on the right of the navbar then click logout. You should now be logged out of the application, If you are thinking, how did we get here? I will explain shortly.

 

## Logout

From the authentication scaffold that was generated earlier, Laravel already created a route and controller to handle clearing the current user session and redirecting you to the login page. If you run php artisan route:list on the terminal you would see the list of all existing routes registered. 

 

Notice from the above snippet that once the user clicks the logout button, we added an inline javascript to submit a hidden form, it sends a POST request to the logout route and this is because the logout route was registered as a post request.

 

Also in the logout form is a csrf\_field function to add an input field with a csrf token into the form and session to prevent Cross Site Request Forgery. Any request made to this form from an outside attacker can’t go through because it will be hard for the attacker to guess the csrf token in a user session to allow the attacker pass through the csrf middleware. 

 

The output of the function looks something like below, inspect the form to see the generated hidden input with the csrf token as the value

 

 
| <input type="hidden" name="\_token" value="S50zdnqbwioh0VQN8OoETHecuBUKbRIRLAGs4TaI"\> |
| --- |

 

## Displaying A Welcome Message

We will be adding a notification message to the dashboard to welcome users when they login, open resources/views/dashboard.blade.php and update it to match below.

 

 
| @extends('layout.master')  
  
@section('page-title')  
    Welcome  
@endsection  
  
@section('content')  
    <div class\="container\-fluid">  
        <div class\="alert alert\-success mt-4" role\="alert">  
            <h4 class\="alert\-heading">Welcome!</h4\>  
            <p\>{{auth()->user()->name}}, you have successfully logged in. There are<strong>3</strong> items in our inventory.</p>  
            <hr>  
        </div>  
    </div>  
@endsection |
| --- |

 

You can access any attribute of a logged in user from the User model via auth()->user(). If you are trying to access a logged user details from a route that is not protected by the auth middleware, to avoid getting an error you should first check if the user is logged in by using auth()->check()  in an if statement.

 

The auth() function is made available by Laravel in every of your pages.  That's how much Laravel makes things easier for you.

 

Before we move into the next section, let us update the url linking to the dashboard on the sidenav. Open resources/views/layout/partials/\_sidenav.blade.php and update the menu with our dashboard url using the named route.

 

 
| <a href="{{route('inventory.home')}}" class\="list\-group\-item list\-group\-item\-action bg\-light">Dashboard</a\> |
| --- |

 

One more benefit of using a named route, is that in the future if we decide to change our dashboard url from /app to /app/dashboard we don't need to go everywhere we used that url to make the changes, we only need to make the changes in our route file, since the named route references the changes we made, we always get the new url every time. See it like a key and value thing in an array where the key is the same but value changes and since we reference the array key we get the updated value every time.

## Create Inventory

Let me break down the steps to allow logged in users create a new inventory, this will help you follow through easily. We will be building this feature in the following order:

 

●         Create an inventories migration to generate the inventories table

●         Create an Inventory Model for the inventories table

●         Define relationship between a user and many inventories in our Model

●         Create an  Inventory Controller class

●         Define a get route to display the, create new inventory page

●         Define a create method in the InventoryController class

●         Create a form with matching fields to our database

●         Define a post route to submit the new inventory

●         Create validation for our inventory

●         Define a store method to create the entry into the database

●         Redirect to new inventory page and display a success notification 

 

Without much ado let us get started! Shall we?

 

 

To create our migration, run

 

 
| php artisan make:migration create\_inventories\_table --create=inventories |
| --- |

 

The \--create option is to indicate whether the migration is for a new table. To edit an existing table the \--table option will be passed instead. That being said, let us add fields to our migration, Laravel provides us with methods to create different data types such as string,int,longText,boolean,foreign key with constraint e.t.c.

 

For our inventories table, edit your migration file located in the database/migrations directory and update the content of the up method to match below. The up method is called when we run the migrate command to create the database while the down method, you can guess already, is called when we run the command to rollback our migration, to drop tables from the database. 

 

 
| //up methodSchema::create('inventories', function (Blueprint $table) {  
            $table->increments('id');  
            $table->string('item');  
            $table->integer('quantity');  
            $table->integer('user\_id');  
            $table->foreign('user\_id')->references('id')->on('users');  
            $table->softDeletes();  
            $table->timestamps();  
        }); |
| --- |

 

To start with, the increments method creates an incrementing column  ID (primary key) using an "UNSIGNED INTEGER" equivalent. 

 

 
| $table->increments('id'); |
| --- |

 

The string method creates a “VARCHAR”  equivalent column ITEM. This method can take a second argument of the size, default is 255.

 

 
| $table->string('item'); |
| --- |

 

The integer methods create an “INTEGER” equivalent column QUANTITY.

 
|  $table->integer(user\_id); |
| --- |

The foreign method is used to specify foreign key constraints, which are used to force referential integrity at the database level. Which references the “PRIMARY KEY” ID on the users table. We added the user\_id column to specify which inventory was created by a particular user using the user PRIMARY ID.

 

 
| $table->foreign('user\_id')->references('id')->on('users'); |
| --- |

 

The softDeletes method adds nullable deleted\_at columns for soft deletes. What this does is ensure that once we call the laravel query builder delete method, the current timestamp will be added to that row on the inventories table instead of dropping the row from the table. This will aid us in building the recycle bin feature.  

 

 
|  $table->softDeletes(); |
| --- |

 

The timestamps method adds nullable created\_at and updated\_at “TIMESTAMP” columns. The created\_at column is updated with the current timestamp when a new row is created, while the updated\_at is updated when the row is updated. Finally, run the migrate command from your terminal or git bash.

 

 
| php artisan migrate |
| --- |

 

Now that our table has been created, if you call the MYSQL DESCRIBE command, our inventories table schema will look like below.

 

 
| +-----------+------------------+------+-----+----------+------------+-  
| Field     |  Type            | Null | Key | Default | Extra          |  
+-----------+------------------+------+-----+----------+------------+-  
| id        | int(10) unsigned | NO   | PRI | NULL    | auto\_increment |  
| item      | varchar(255)     | NO  |     | NULL    |                |  
| quantity  | int(11)          | NO   |     | NULL    |                |  
| user\_id   | int(10) unsigned | NO   | MUL | NULL    |                |  
| deleted\_at| timestamp        | YES  |     | NULL    |                |  
| created\_at| timestamp        | YES  |     | NULL    |                |  
| updated\_at| timestamp        | YES  |     | NULL    |                |  
+--------+---------------------+------+-----+----------+------------+- |
| --- |

 

 

Now let's move on to creating an Inventory Model for the inventories table

##  

 

## Create an Inventory Model & Define The Relationship

Laravel Model represents the logical structure and relationship of the underlying data table it represents, it allows you to query for data in your tables easily, as well as insert new ones. There is a Model to a table which enables you to use the Laravel ORM (Object Relational Database) to interact with such a table.

 

In order to create a Model, Laravel allows you to do using the artisan command. Run this command on your terminal or git bash

 

 
| php artisan make:model Inventory |
| --- |

 

Under the app directory you would find the Inventory.php class there. This is the default location where generated models are stored, you can group them in an app/model directory or wherever you desire, but to keep things simple we would leave it here.  

 

Next let us define the relationship on this table in our model, again Laravel allows us to define different types of  relationships on multiple tables. You can define a one to many relationship using the hasMany method, or one to one using the hasOne method or many to many using the belongsToMany method and several others in your table corresponding Model.

 

In our own case a user can create/own multiple inventories and inversely an inventory will belong to a user, so we have a user hasMany inventories and  an inventory belongsTo a user. Let us define that in our model.

 

 

 

 

 

 

 

 

 

 

 

 

��Note

To learn more about other available methods for creating different columns types in your database, you can checkout the available column types in the [Laravel docs](https://laravel.com/docs/5.4/migrations#creating-columns).

In our app/User.php model class, add the method inventories.

 

 
| public function inventories()  
{  
   return $this\->hasMany(Inventory::class);  
} |
| --- |

 

Open app/Inventory.php model class, to define the opposite relationship.

 

 
| public function ownedBy()  
{  
     return $this\->belongsTo(User::class);  
} |
| --- |

 

Additionally in the inventory model class, add a protected property guarded as below.

 

 
| protected $guarded  = \['id'\]; |
| --- |

 

Don’t get confused just yet, the guarded property is an inherited protected property already defined by the Laravel Model class, which our Inventory model class extends. Laravel allows you, using the query builder to mass assign data into the database, simply by passing an array of data you want to insert, which will be inserted into the database.

 

Sometimes this can be bad, as a malicious user can guess a field in your table and inject an harmful data to be passed into your database, so in order to exempt some important field from being mass assignable, like the id field in our own case, since we don’t want someone inserting their own id and destroy our auto increment behaviour we simply make the field not mass assignable. Lastly because of the soft delete feature we want to implement, we included the SoftDelete trait for this purpose.

 

 

 

 

 

 

 

 

 

 

 

Your entire Inventory model class  should match below

 

 
| <?php  
  
namespace App;  
  
use Illuminate\\Database\\Eloquent\\Model;  
use Illuminate\\Database\\Eloquent\\SoftDeletes;  
class Inventory extends Model  
{    use SoftDeletes;  
    protected $guarded  = \['id'\];  
  
    public function ownedBy()  
    {  
        return $this\->belongsTo(User::class);  
    }  
}  |
| --- |

##  

##  

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

## Defining the Route, Inventory Controller & Request Validation

Let us handle the business logic of creating our inventory. First run the artisan command to create an Inventory Controller. To do so run the command below

 

 
| php artisan make:controller InventoryController |
| --- |

 

Under app/Http/Controllers the class InventoryController.php will be generated by Laravel, edit this file and add the following placeholder method. We will be updating them later.

 

 

 
| <?php  
  
namespace App\\Http\\Controllers;  
  
use Illuminate\\Http\\Request;  
  
class InventoryController extends Controller  
{  
    public function createInventory()  
    {  
       return view('new-inventory');  
    }  
  
    public function storeInventory()  
    {  
        //validate & store in db  
    }  
  
    public function viewInventories()  
    {  
        //retrieve and list   
    }  
  
} |
| --- |

 

 

 

 

 

In our route file app/routes/web.php add the url to create, store and view our inventory. Update the route groups to match below

 

 

 
| Route::group(\['prefix' => 'app','middleware' => 'auth'\],function($route){  
  $route->get('/', 'AppController@dashboard')        ->name('inventory.home');  $route->get('/create', 'InventoryController@createInventory')        ->name('inventory.create');  $route->post('/create', 'InventoryController@storeInventory')        ->name('inventory.store');  $route->get('/inventories', 'InventoryController@viewInventories')        ->name('inventory.all');//The value in the curly braces must match the model of the table we           are deleting from as this will allow Laravel knows which class to resolve$route->delete('/inventories/{inventory}/drop','InventoryController@drop')        ->name('inventory.delete');}); |
| --- |

 

Next let’s create a Form Request Validation to validate the request sent to the  storeInventory method. We would be defining rules to validate the input of the user entered from the create form we would be creating shortly, one rule of thumb is to never trust users input and always endeavour to validate them. To create our Form Request run the below command

 

 
| php artisan make:request StoreInventory |
| --- |

 

A new class StoreInventory.php will be created under the app/Http/Requests directory. Edit this file, first under the authorize method change return false to return true now let us define rules for the two input fields item and quantity, that will be in our form.

 

We want the item field to always be a string not more than 255 characters which is the maxlength of mysql VARCHAR to avoid mysql truncating the data and quantity field should be an integer, not more than 100 can be allowed assuming we do not want to ever create an inventory with over 100 stock and both fields are required. Replace the empty array returned in the rules method with below

 

 
| return \[  
            'item' => 'required|string|max:255',  
            'quantity' => 'required|int|max:100'  
        \]; |
| --- |

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

��Note

To learn more about other validation rules available in Laravel, visit the [Available Validation Rules](https://laravel.com/docs/5.4/validation#available-validation-rules) section of the official Laravel documentation.

## Create Inventory Form & List Inventories

Create a new file new-inventory.blade.php under app/resources/views, this child view will extend our master layout and hold the form to create inventory. Copy the code below into the file

 

 
| @extends('layout.master')  
  
@section('page-title')  
    New Inventory  
@endsection  
  
@section('content')  
    <div class\="container\-fluid">  
   <div class\="col\-12 col\-md\-8 mt\-4">  
       <form method\="POST" action\="{{route('inventory.store')}}">           {{csrf\_field()}}  
           <div class="form-group">  
               <label for="item">Item</label>  
               <input type="text" value="{{old('item')}}" class="form-control" name="item" id="item" placeholder='e.g 32" Television'>  
               @if ($errors->has('item'))  
                   <small class="form-text text-danger">  
                       {{ $errors->first('item') }}  
                   </small>  
               @endif  
           </div>  
           <div class="form-group">  
               <label for="quantity">Quantity</label>  
               <input type="text" value="{{old('quantity')}}"  class="form-control" name="quantity" id="quantity" placeholder="e.g 50">              @if ($errors->has('quantity'))  
                   <small class="form-text text-danger">  
                       {{ $errors->first('quantity') }}  
                   </small>  
               @endif  
           </div>  
           <button type="submit" class="btn btn-primary">Create New Inventory</button>  
       </form>  
   </div>  
    </div>  
@endsection |
| --- |

 

Few things to take note of in our new inventory view, is one, the form submits a POST request to the named route inventory.store which we defined earlier as a POST route in the web.php file and  secondly you will notice an if else statement checking if the field doesn’t pass the validation we defined in the StoreInventory.php rules, Laravel automatically redirects back to the create inventory page with the error messages in the request, so our if statement checks if the field error exists in shows the first error that fails validation. 

 

Your field could pass one validation rule and fail the other, the error for that rule would be returned but if all validation passes, the request proceeds to execute the next code block. Notice the use of old(‘item’) and old(‘quantity’) in our value field, what this does is when we have an error in the form and the page redirects back, it gets the value entered by the user into the field so user doesn’t have to retype all the values everytime the validator redirects them back.

 

While we are at this, I would like to talk about a very interesting topic  that might seem confusing at first especially if you are new to it.

### Dependency Injection & Controllers

 

Dependency injection is a technique whereby one object supplies the dependencies of another object. A "dependency" is an object that can be used in another object. For example if you have a class Car with methods start, accelerate and horn, and another class AutoShop with methods repair, setNextRepairDate and testDrive. You might initially be tempted to pack all methods that belong to the AutoShop Class inside the Car class but with DI(Dependency Injection) we can follow the Single Responsibility principle of the SOLID design pattern. In our case we can inject the Car object into the AutoShop class and call the accelerate method in the testDrive method, since test driving a car requires you to accelerate the car.

 

Laravel allows you to inject through the controller constructor (Constructor Injection) and controller methods (Method Injection) which will be automatically resolved via the service container. Below we would be injecting the StoreInventory object in the store method, then Laravel knowing that we injected a Form Request class will use the rule in the class to validate the incoming request.

 

Don’t get confused just yet! It's just what Laravel provides for us outside the box so we don’t have to write multiple codes to perform all this action. 

 

 

��Note

To learn more on Dependency Injection, visit the laravel documentation [here](https://laravel.com/docs/5.4/controllers#dependency-injection-and-controllers).

 

### The List Inventory View

Create a new file view-inventories.blade.php inside the app/resources/view directory and paste the below code.

 

 
| @extends('layout.master')  
  
@section('page-title')  
    New Inventory  
@endsection  
  
@section('content')  
    <div class\="container\-fluid">  
        <div class\="col\-12 col\-md\-8 mt\-4">  
            <table class\="table table\-hover table\-bordered">  
                <thead\>  
                <tr\>  
                    <th scope\="col">#</th\>  
                    <th scope\="col">Item</th\>  
                    <th scope\="col">Quantity</th\>  
                    <th scope\="col">Actions</th\>  
                </tr\>  
                </thead\>  
                <tbody\>  
                @foreach($inventories as $key => $inventory)  
                    <tr\>  
                        <th scope\="row">{{$key + 1}}</th>  
                        <td>{{$inventory->item}}</td>  
                        <td>{{$inventory->quantity}}</td>  
                        <td>  
                            <a href="#" class\="btn btn\-outline\-primary btn\-sm">Edit</a\>  
                            <a href\="#" class\="btn btn\-outline\-danger btn\-sm" onclick\='event.preventDefault(); document.getElementById("delete\-inventory\-form\-{{$key}}").submit();'>  
                                Delete  
                                <form id="delete-inventory-form-{{$key}}" action="{{ route('inventory.delete',$inventory->id) }}" method="POST" style="display: none;">  
                                    {{ csrf\_field() }}  
                                </form>  
                            </a>  
                        </td>  
                    </tr>  
                @endforeach  
                </tbody>  
            </table>  
        </div>  
    </div>  
@endsection |
| --- |

 

Next update your layout/partials/\_sidenav.blade.php , so as to add the create and logout routes for easy navigation.

 

 
| <div class\="bg\-light border\-right" id\="sidebar\-wrapper">  
    <div class\="sidebar\-heading">{{config('app.name')}}</div>  
    <div class\="list\-group list\-group\-flush">  
        <a href\="{{route('inventory.home')}}" class="list\-group-item list\-group-item-action bg-light">Dashboard</a>  
        <a href="{{route('inventory.all')}}" class="list\-group-item list\-group-item-action bg-light">View Inventories</a>  
        <a href="{{route('inventory.create')}}" class="list\-group-item list\-group-item-action bg-light">New Inventory</a>  
        <a href="#" class="list-group-item list-group-item-action bg-light">Trash</a>  
        <a href="#" class\="list\-group\-item list\-group\-item\-action bg\-light" onclick\="event.preventDefault(); document.getElementById('logout\-form').submit();">  
            Logout  
            <form id\="logout\-form" action\="{{ route('logout') }}" method="POST" style="display: none;">  
                {{ csrf\_field() }}                {{method\_field('DELETE')}}  
            </form>  
        </a>  
    </div>  
</div> |
| --- |

 

Soon you will see from our controller how the inventory array of objects, containing a list of all   inventories in the database , is passed to our view. We used blade template @foreach directive to loop through the array and display the item, quantity and action buttons for each entry. One strange thing to note here is the method\_field which is used for Form Method Spoofing.

 

HTML forms do not support PUT, PATCH or DELETE actions. So, when defining PUT, PATCH or DELETE routes that are called from an HTML form, you will need to add a hidden \_method field to the form. The value sent with the \_method field will be used as the HTTP request method:

 

If you refresh your browser now and click on the view inventories menu you will be presented with an empty table. Now let's get to the inserting into database part.

 

Update your InventoryController to match below code, I will explain in details afterwards.

 

 
| <?php  
  
namespace App\\Http\\Controllers;  
  
use App\\Http\\Requests\\StoreInventory;  
use App\\Inventory;  
use Illuminate\\Http\\Request;  
  
class InventoryController extends Controller  
{  
    public $inventory;  
  
    public function \_\_construct(Inventory $inventory)  
    {  
        $this\->inventory = $inventory;  
    }  
  
    public function createInventory()  
    {  
        return view('new-inventory');  
    }  
  
        public function storeInventory(StoreInventory $storeInventory)  
    {        $data = $storeInventory->only('item','quantity');  
        auth()->user()-\>inventory()->create($data);        $msg = 'New inventory successfully added!';  
  
        return redirect()->route('inventory.all')->with('message',$msg);  
    }  
  
    public function viewInventories()  
    {  
        $inventories = $this\->inventory->all();  
  
        return view('view-inventories',compact('inventories'));  
    }  
  
    /\*\*  
     \* @param Inventory $inventory  
     \* @return \\Illuminate\\Http\\RedirectResponse  
     \* @throws \\Exception  
     \*/  
    public function drop(Inventory $inventory)  
    {  
        $inventory->delete();  
  
        return redirect()->route('inventory.all')               ->with('message','New inventory successfully added!');  
    }  
}  |
| --- |

 

 

We imported both the Inventory model class and StoreInventory Form request class using PHP use keyword.

 

 
| use App\\Http\\Requests\\StoreInventory;  
use App\\Inventory; |
| --- |

 

 

We defined the property $inventory to hold the $inventory model object which was injected through the controller.

 

 
|     public $inventory;  
  
    public function \_\_construct(Inventory $inventory)  
    {  
        $this\->inventory = $inventory;  
    }  
  |
| --- |

 

Here we did a method injection of the StoreInventory object. Laravel will automatically resolve and detect if it’s a Form Request then apply the rules to validate the incoming data, again this is Laravel trying to make a developer life easier. 

 

Usually when a user submits a form, you can access the request data using the php $\_POST or $\_GET  super global variable, with Laravel you can access the data from the Request object which you can inject into your controller constructor or controller methods. In our storeInventory method the StoreInventory Form Request object is injected and it extends the Request class, so we don’t need to inject the Request object the second time, to access our  get or post data from the current http request.

 

Laravel provides us with different methods on the request class to access data. There is method all to retrieve all data from request, method only to specify keys to retrieve, method get to access request param. There are others such as except, intersect ,input e.t.c. 

 

We will call the create method on the inventory model via the user-inventory relationship, this way the user\_id foriegn field will be the current logged in user. After inserting into the database, we redirect users  to the list all inventories page with a successful notification message displayed to them.

 
|  public function storeInventory(StoreInventory $storeInventory)  
 {  
        $data = $storeInventory->only('item','quantity');  
        auth()->user()->inventory()\->create($data);  
        $msg = 'New inventory successfully added!';  
  
        return redirect()->route('inventory.all')->with('message',$msg);  
 } |
| --- |

 

Here we are getting all inventories from the database, by calling the all method from the inventory model.  There are other methods such as latest to fetch them in ascending order, first to get the first row matching a where condition, select to choose fields you want returned and get method. Laravel provides us with many more query builders that makes it convenient to query data from the database, you don’t have to write or try to remember any SQL query in most cases, as I will be careful not to say never again.

 

 
| public function viewInventories()  
{  
    $inventories = $this\->inventory->all();  
  
    return view('view-inventories',compact('inventories'));  
} |
| --- |

 

There are two concepts I would like to shed more light to when it comes to deleting an inventory. First is how we defined our route and how we used it in the loop of the list inventories page.

 

In our route definition, the second segment of the URL is a route parameter that will be replaced with id of each inventory. It will be generated by the route function, all we need do is pass the id as a second parameter to the route function, you can have more than one route parameter, and in that case pass an array with the parameters in the other that they appear as the second parameter to the route function.

 

In addition to that, Laravel helps do something called Route Model Binding. When we inject an id to our route like we are doing in this case, Laravel resolves the Eloquent Model, based on the type hint in the url, in our case {inventory}. In simple english, if our URL is /inventories/1/drop, Laravel will look for the row with id 1 from the inventory model (inventories table) and return it to us in the controller.

 

 
| //Route definition  
$route->delete('/inventories/{inventory}/drop','InventoryController@drop')->name('inventory.delete');  
  
//Route usage  
{{ route('inventory.delete',$inventory->id) }} |
| --- |

 

Here we just simply type hint the model to be injected based on the route model binding, and we call the method delete on the model object returned which in return delete the corresponding row in the inventories table.

 

Finally we redirect to the page with all inventories with a notification message.

 

 
| public function drop(Inventory $inventory)  
{  
   $inventory->delete();  
  
   return redirect()->route('inventory.all')  
               ->with('message','New inventory successfully added!');  
} |
| --- |

 

Open the resources/views/view-inventories.blade.php in your editor, and just above the opening table tag place the code snippet below to display notification messages flashed into session from our controller.

 

 
| @if(session()->has('message'))  
      <div class\="alert alert\-info">  
          {{session('message')}} New inventory successfully added!  
      </div>  
 @endif |
| --- |

 

Refresh the app in the browser or login back if you are logged out, click on the New Inventory menu then submit an empty form. You should be redirected back with error showing under the input field.

![](Images/image00201.jpeg)

 

Now fill the form and click on the create new inventory button. You should be redirected to the list inventories page with a successful notification message.

 

![](Images/image00202.jpeg)

 

Go ahead to create as many as you want and delete a few. You should be impressed on how far we have come. Before we move on to the Trash feature, let us quickly update our dashboard to reflect the actual numbers of  inventories created.

 

Update the AppController class to match below

 

 
| <?php  
  
namespace App\\Http\\Controllers;  
  
use App\\Inventory;  
use Illuminate\\Http\\Request;  
  
class AppController extends Controller  
{  
    public function dashboard(Inventory $inventory)  
    {  
        $count = $inventory->count();  
  
        return view('dashboard',compact('count'));  
    }  
} |
| --- |

 

 

 

 

 

And line 11 on the dashboard.blade.php file

 

 
| <p>{{auth()->user()->name}}, you have successfully logged in. There is <strong>{{$count}}</strong>{{str\_plural('item',$count)}} in our inventory.</p> |
| --- |

 

## Building The Trash Feature

If you open your database in your prefered database manager e.g phpmyadmin, mysql workbench or squealpro you will in fact notice that the inventory you deleted from the frontend is still there, only that the deleted\_at column is not null. This a function of Laravel soft delete that we discussed earlier.

 

Let create a page to list all deleted inventories with an action to restore them back. Sounds cool right? We can use the same content of the list inventory page, with slight edit to the action buttons, one to restore and the other permanently delete. But first lets add additional routes and controller methods.

 

Add this after the delete route

 

 
| $route->get('/inventories/{inventory}/restore','InventoryController@restoreItem')->name('inventory.restore');  
    $route->delete('/inventories/{inventory}/purge','InventoryController@purgeItem')->name('inventory.purge'); $route->get('/inventories/trash','InventoryController@viewTrash)\->name('inventory.trash'); |
| --- |

 

Next, add the methods of this routes to the InventoryController.

 

 
|   public function viewTrash(Inventory $inventory)  
    {  
        $inventories = $inventory->onlyTrashed()->get();  
  
        return view('trash',compact('inventories'));  
    }  
  
    public function restoreItem($inventory)  
    {  
        if($item = $this->inventory->withTrashed()->find($inventory)) {            $item->restore();        }  
  
        return redirect()->route('inventory.all')               ->with('message','Inventory successfully restored!');  
    }  
     
    public function purgeItem($inventory)  
    {  
        if($item = $this->inventory->withTrashed()->find($inventory)) {            $item->forceDelete();        }  
  
        return redirect()->route('inventory.all')               ->with('message','Inventory permanently deleted!');  
    } |
| --- |

 

In the case of restoring and permanently deleting an item, we can’t do a Route Model Binding, because Laravel considers this model already deleted from the database, so it will always return a not found exception, in other words we simply capture the segment with the inventory id then use the withTrashed method to force soft deleted models to appear in a result.

 

Create a new file trash.blade.php under your resources/views directory and go ahead to paste the below code.

 

 
| @extends('layout.master')  
  
@section('page-title')  
    Trash  
@endsection  
  
@section('content')  
    <div class\="container\-fluid">  
        <div class\="col\-12 col\-md\-8 mt\-4">  
            @if(session()->has('message'))  
                <div class\="alert alert\-info">  
                    {{session('message')}}  
                </div>  
            @endif  
            <table class\="table table\-hover table\-bordered">  
                <thead\>  
                <tr\>  
                    <th scope\="col">#</th\>  
                    <th scope\="col">Item</th\>  
                    <th scope\="col">Quantity</th\>  
                    <th scope\="col">Actions</th\>  
                </tr\>  
                </thead\>  
                <tbody\>  
                @foreach($inventories as $key => $inventory)  
                    <tr\>  
                        <th scope\="row">{{$key + 1}}</th>  
                        <td>{{$inventory->item}}</td>  
                        <td>{{$inventory->quantity}}</td>  
                        <td>  
                            <a href="{{route('inventory.restore',$inventory->id)}}" class\="btn btn\-outline\-primary btn\-sm">Restore</a\>  
                            <a href\="#" class\="btn btn\-outline\-danger btn\-sm" onclick\='event.preventDefault(); document.getElementById("delete\-inventory\-form\-{{$key}}").submit();'>  
                                Purge  
                                <form id="delete-inventory-form-{{$key}}" action="{{ route('inventory.purge',$inventory->id) }}" method="POST" style="display: none;">  
                                    {{ csrf\_field() }}  
                                    {{method\_field('DELETE')}}  
                                </form>  
                            </a>  
                        </td>  
                    </tr>  
                @endforeach  
                </tbody>  
            </table>  
        </div>  
    </div>  
@endsection |
| --- |

 

Now click on the Trash menu on the sidenav to view items in the trash, try to permanently delete or restore the items to see how this feature works. 

 

 

 

 

 

 

 

 

 

 

 

 

## Edit Inventory

Editing our inventory is as easy as creating it, first we need to create a get route for the edit form with a Route Model Binding implementation, then a post route for the form submission. We would still use the StoreInventory request validation class since the same validation rule applies, otherwise you can create a new one if you are looking to have some fun adding new validation rules.   

 

We will duplicate the content of the new-inventory.blade.php page into app/resources/edit-inventory.blade.php file, then make a few adjustments. Let us quickly do that!

 

 
|  $route->get('/inventories/{inventory}/edit','InventoryController@editInventory')->name('inventory.edit');  
 $route->put('/inventories/{inventory}/edit','InventoryController@updateInventory')->name('inventory.update'); |
| --- |

 

Open view-inventories.blade.php on line 31, update the edit action href

 

 
| <a href="{{route('inventory.edit',$inventory->id)}}" class\="btn btn\-outline\-primary btn\-sm">Edit</a\> |
| --- |

 

 

 

 

 

 

 

 

 

 

 

 

 

 

Add these methods to your InventoryController, for the edit and update actions.

 

 

 
| public function editInventory(Inventory $inventory)  
{  
   return view('edit-inventory',compact('inventory'));  
}  
  
/\*\*  
\* @param StoreInventory $storeInventory  
\* @param Inventory $inventory  
\* @return \\Illuminate\\Http\\RedirectResponse  
\*/  
public function updateInventory(StoreInventory $storeInventory,Inventory $inventory)  
{  
   $inventory->update($storeInventory->only('item','quantity'));  
  
    return redirect()->route('inventory.all')             ->with('message','Inventory successfully updated!');  
} |
| --- |

 

Finally edit your edit-inventory.blade.php to match below.

 

 
| @extends('layout.master')  
  
@section('page-title')  
    Edit Inventory  
@endsection  
  
@section('content')  
    <div class\="container\-fluid">  
        <div class\="col\-12 col\-md\-8 mt\-4">  
            <form method\="POST" action\="{{route('inventory.update',$inventory->id)}}">  
                {{csrf\_field()}}  
                {{method\_field('PUT')}}  
                <div class="form-group">  
                    <label for="item">Item</label>  
                    <input type="text" class="form-control" value="{{old('item',$inventory->item)}}" id="item" name="item" placeholder='e.g 32" Television'>  
                    @if ($errors->has('item'))  
                        <small class="form-text text-danger">  
                            {{ $errors->first('item') }}  
                        </small>  
                    @endif  
                </div>  
                <div class="form-group">  
                    <label for="quantity">Quantity</label>  
                    <input type="text" class="form-control"  value="{{old('item',$inventory->quantity)}}" id="quantity" name="quantity" placeholder="e.g 50">  
                    @if ($errors->has('quantity'))  
                        <small class="form-text text-danger">  
                            {{ $errors->first('quantity') }}  
                        </small>  
                    @endif  
                </div>  
                <button type="submit" class="btn btn-primary">Update Inventory</button>  
            </form>  
        </div>  
    </div>  
@endsection |
| --- |

 

Go ahead to edit one of your existing inventory, test if the validation works fine by emptying the quantity field. Now change the previous value of the quantity field to a new value then submit the form, you should be redirected to the list inventories page with a  successful notification.

 

 

 

 

 

 

In my own case, I updated the quantity for the Playstation from 4 to 6.

 

![](Images/image00203.jpeg)

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

#  

#  

#  

 

 

# CRON JOB & Task Scheduling

 

Laravel provides us with a way to effortlessly, create command schedules within Laravel itself. If you have had experience creating cron jobs on a server, you would realise how editing your crontab file every now and then to add more tasks is not fluent enough. 

 

 

When using the scheduler, only a single Cron entry is needed on your server, this cron entry runs every minute and checks if any task is due then executes it. Our task schedule is defined in the app/Console/Kernel.php file's schedule method.

 

Open your Terminal and enter command 

 

 
| crontab -e |
| --- |

 

This is to edit your crontab file, paste the below command inside the opened file on your terminal. In my own case, my project directory is placed inside my system home/Sites directory, you should replace as seen below, also substitute path to php bin, you can always find that out by running which php command from your terminal.

 

 
| //Replace with your directory path//Run which php command in terminal to know path exec path  
\* \* \* \* \* /path-php-bin/php /path-to-inventory-app-directory/artisan schedule:run >> /dev/null 2\>&1  
  
//Here is how mine looks like  
\* \* \* \* \* /usr/local/bin/php ~/Sites/inventory-app/artisan schedule:run >> /dev/null 2\>&1 |
| --- |

 

This will run the php artisan schedule command every minute to check if there's any schedule due to be executed. You will soon have a better understanding once we create our first Job.

 

By default for Linux and Mac users, the vim editor will be launched to edit the file, If this is your first experience with the vim editor and you are finding it difficult to paste into the editor, press the escape key then i key on your keyboard, paste the command and edit it to reflect your directory path, finally press escape again and shift + colon key on the keyboard then enter wq and hit the enter key. You will get the response crontab: installing new crontab.

 

## Defining a Job

We will define a job to check if an inventory has been in the trash ( equivalent of  soft delete) for more than 3 mins then, force delete it from the database. In real life we would probably check for items in trash that have used more than 3 - 5 days but for this tutorial we can’t wait that long, the same codebase for 3 minutes will work for 3 days check, you only need to change the time difference.

 

Run command below in your terminal

 

 
|  php artisan make:job ClearTrash |
| --- |

 

If you check app/Jobs directory, you will see the generated ClearTrash class. The handle method will hold the code that will get executed, every minute to check if we have item in trash deleted over 3 mins ago.

 

 
| <?php  
  
namespace App\\Jobs;  
  
use App\\Inventory;  
use DateInterval;  
use DateTime;  
use Illuminate\\Bus\\Queueable;  
use Illuminate\\Queue\\SerializesModels;  
use Illuminate\\Queue\\InteractsWithQueue;  
use Illuminate\\Contracts\\Queue\\ShouldQueue;  
use Illuminate\\Foundation\\Bus\\Dispatchable;  
  
class ClearTrash implements ShouldQueue  
{  
    use Dispatchable, InteractsWithQueue, Queueable, SerializesModels;  
  
  
    /\*\*  
     \* Create a new job instance.  
     \*  
     \*/  
    public function \_\_construct()  
    {  
        //  
    }  
  
    /\*\*  
     \* Execute the job.  
     \*  
     \* @param Inventory $inventory  
     \* @return void  
     \* @throws \\Exception  
     \*/  
    public function handle(Inventory $inventory)  
    {  
        $now = new DateTime('now');  
        $threeMinutesDiff = new DateInterval('PT03M');  
        $threeMinutesAgo = $now->sub($threeMinutesDiff)->format('Y-m-d H:i:s');  
  
        $inventories = $inventory->onlyTrashed()->where('deleted\_at','<=',$threeMinutesAgo)->get();  
  
        foreach($inventories as $inventory){  
            $inventory->forceDelete();  
        }  
    }  
} |
| --- |

 

On your terminal from our inventory project directory, run command 

 

 
| php artisan queue:listen |
| --- |

 

 

This command runs the queue worker that will process new jobs as they are pushed onto the queue. In a real live scenario, we would be using a process monitor such as Supervisor to ensure that the queue worker does not stop running permanently in the background.

 

To confirm if this works, go ahead to delete an inventory, view your trash to see if the item is in trash, wait for an additional 3 mins, then refresh your trash. You will notice the trash is now empty and if you check your database from your database manager, you won’t see it there either.

 

## Sending Email

Sending email with Laravel can’t be more easier and fun.  Let us send an email to a user informing the user that items in trash has just been cleared. 

 

Laravel supports both SMTP and PHP's "mail" function as drivers for the sending of email. You may specify which one you're using throughout your application here. By default, Laravel is set up for SMTP mail. Laravel provides support for sending email via API or SMTP for the following service providers; sendmail, mailgun, mandrill, amazon ses and sparkpost. I personally prefer using mailgun, you can decide to use it or choose another service provider.

 

But for the purpose of this tutorial, we would be using a fake smtp server called [mailtrap.io](http://mailtrap.io). Open a free account, set it up and choose Laravel as your framework then get your SMTP details as below and enter it into the corresponding key in your .env. Changing to a live smtp server is as easy as replacing the smtp details in your .env with the new one provided by the service provider.

 

![](Images/image00204.jpeg)

 

 

 

 

 

 

In the .env locate and replace the value appropriately.

 

 
| MAIL\_DRIVER=smtp  
MAIL\_HOST=smtp.mailtrap.io  
MAIL\_PORT=2525  
MAIL\_USERNAME=33fcd1c32ab794  
MAIL\_PASSWORD=8a169e3a907b5d  
MAIL\_ENCRYPTION=null  
  
MAIL\_FROM\_ADDRESS=notification@laraventory.com  
MAIL\_FROM\_NAME=Laraventory |
| --- |

 

ANytime you make changes to your .env file, stop the current running php artisan serve command and run it again. Next from your terminal, run the command below to create an email and a markdown template  for the email.

 

 
| php artisan make:mail TrashNotification --markdown email/trash-notification |
| --- |

 

Under app/Mail a TrashNotification class to handle our email will be auto generated and under resources/views/email the trash-notification.blade.php file with a placeholder markdown will also be generated. 

 

Update the email template to show a better message, you can likewise edit to your preference.

 

 
| @component('mail::message')  
\# Notification  
  
This is a friendly notification to notify you that I just completed clearing the inventory trash.  
  
@component('mail::button', \['url' => route('inventory.trash')\])  
View Trash  
@endcomponent  
  
Thanks,<br\>  
{{ config('app.name') }}  
@endcomponent |
| --- |

 

 

Finally update the ClearTrash.php class in the Jobs directory to send an email after clearing the trash.

 

 
| <?php  
  
namespace App\\Jobs;  
  
use App\\Inventory;  
use DateInterval;  
use DateTime;  
use Illuminate\\Bus\\Queueable;  
use Illuminate\\Queue\\SerializesModels;  
use Illuminate\\Queue\\InteractsWithQueue;  
use Illuminate\\Contracts\\Queue\\ShouldQueue;  
use Illuminate\\Foundation\\Bus\\Dispatchable;  
use Illuminate\\Support\\Facades\\Mail;  
  
class ClearTrash implements ShouldQueue  
{  
    use Dispatchable, InteractsWithQueue, Queueable, SerializesModels;  
  
  
    /\*\*  
     \* Create a new job instance.  
     \*  
     \*/  
    public function \_\_construct()  
    {  
        //  
    }  
  
    /\*\*  
     \* Execute the job.  
     \*  
     \* @param Inventory $inventory  
     \* @return void  
     \* @throws \\Exception  
     \*/  
    public function handle(Inventory $inventory)  
    {  
        $now = new DateTime('now');  
        $threeMinutesDiff = new DateInterval('PT03M');  
        $threeMinutesAgo = $now->sub($threeMinutesDiff)->format('Y-m-d H:i:s');  
  
                 $inventories = $inventory->onlyTrashed()                         ->where('deleted\_at','<=',$threeMinutesAgo)->get();  
  
        foreach($inventories as $inventory){  
            $inventory->forceDelete();  
        }  
  
        if($inventories->count() > 0){           Mail::to('oluwafemialofe@gmail.com') //Substitute with your email            ->send(new \\App\\Mail\\TrashNotification());        }  
    }  
} |
| --- |

 

Stop running your previous php artisan queue:work command and php artisan serve command then rerun the commands again from your project directory on the terminal. 

 

Now proceed to create new inventories, delete a few of them, confirm they are in the trash then wait for 3 mins. After 3 mins the trash will be cleared and if you open your mailtrap.io account and check the inbox you will see an email.

 

![](Images/image00205.jpeg)

 

Congratulations!

# Conclusion

So far, we have been able to cover several basics and some slightly advanced topics in Laravel. Needless to say, you need to extend the project and add more features, on your own to further improve your knowledge and test your skill.

 

Also do well to browse through the official documentation of Laravel to know other nice features that might you will find interesting.

 

If you need any help, at any point in this book or need me for a Laravel project, don’t hesitate to shoot me an email at [oluwafemialofe@gmail.com](mailto:oluwafemialofe@gmail.com).

 

 

Sabali!