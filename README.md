## How to Create Project, Run and Migration

* Create New Project
> rails new project

* Run Project
> rails server

* Create (db/migrate)
> rails generate migration create_articles

* After creted and modified then
> rails db:migrate

* if we want to alter table then rollback first
> rails db:rollback

* Create (db/migrate)
> rails generate migration alter_articles

* After that
> rails db:migrate


## How to Create Model

* Manual Create article.rb inside /app/models/article.rb ,
* Then write this code to automated setter getter
```
class Article < ApplicationRecord
end
```

* we also can put validation inside model
```
validates :title, presence: true, length: { minimum: 3, maximum: 50 }
validates :description, presence: true, length: { minimum: 10, maximum: 300 }
```


## How to Create Home Controller

* Open /config/routes.rb write this. (pages is controller and home is method inside page controller)
```
get 'pages/home', to: 'pages#home'
```

* And Create pages_controller.rb inside /app/controller/pages_controller.rb then write this inside it:
```
class PagesController < ApplicationController
  def home
  end
end
```

* Now we create folder pages inside /app/views/pages
* Then we create filse home.html.erb inside /app/views/pages/home.html.erb and write a simple scripts
```
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Flash</title>
  </head>
  <body>
    <h1>Welcome to my <a href="#">Blog</a></h1>
  </body>
</html>
```
* Run command `rails server` and then try to open url: http://localhost:3000/pages/home


## How make home to be root
* just remove or change `get 'pages/home', to: 'pages#home'` to `root 'pages#home'`
* Run command `rails server` and then try to open url: http://localhost:3000/


## How to Create Article Controller and CRUD

* Open /config/routes.rb write this:
`resources :articles`

* Then we run this to check existing routes for articles
> rails routes

* Or if using windows to filter :
> rails routes | FIND /I "article"

* then this output should be
```
---------------------------------------------------------------------------
Prefix 			   Verb     URI Pattern                      #Action
---------------------------------------------------------------------------
articles 		   GET      /articles(.:format)              articles#index
				       POST     /articles(.:format)              articles#create
new_article 	 GET      /articles/new(.:format)          articles#new
edit_article 	 GET      /articles/:id/edit(.:format)	 	 articles#edit
article 		   GET      /articles/:id(.:format)          articles#show
				       PATCH    /articles/:id(.:format)          articles#update
				       PUT      /articles/:id(.:format)          articles#update
				       DELETE   /articles/:id(.:format)          articles#destroy
---------------------------------------------------------------------------
```
