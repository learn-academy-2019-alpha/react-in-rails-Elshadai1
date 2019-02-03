# React-Rails Hello World example

Up until this point, we've been using create-react-app to build our applications, and we've been using a separate Rails applications to exmplore Rails and APIs.  Have you wondered if Rails, as full featured as it is, could be the platform for the API and the React app together?  If so, it was a good question to ask, and as you may have guessed, Rails can also serve right from normal old erb pages.  Not only can it do so, but the solution is very elegant, and using Rails in this way allows us as developers to build larger and more interesting applications in an organized way.

Let's explore how Rails and React are integrated by constructing the simplest possible Rails app, and the simplest possible React component and getting them to work together.

## React-Rails Docs
Please have a read of the [docs for the react-rails project](https://github.com/reactjs/react-rails) first to see what we're going to do, and all of the advanced features of the gem.


## Setup Steps

1) Create a Rails Application
```bash
$ rails new hello_world
$ cd hello_world
```

2) Add the React Gems
```bash
$ bundler add webpacker
$ bundler add react-rails
$ bundle install
```

3) Install Webpacker
```bash
$ rails webpacker:install
$ rails webpacker:install:react
$ rails generate react:install
```

4) Add Webpack to the Rails Application Layout (/app/views/layouts/application.html.erb)
```html
<%= javascript_pack_tag 'application' %>
```

5) Generate a new React component
```bash
$ rails g react:component HelloWorld
```

6) Update the new Component
```bash
cat app/javascript/components/HelloWorld.js
```
```result
: import React from "react"
: import PropTypes from "prop-types"
: class HelloWorld extends React.Component {
:   render () {
:     return (
:       <h1>Hello World</h1>
:     );
:   }
: }
:
: export default HelloWorld
```

7) Create a Homepage and add the Route to Rails

```bash
$ rails g controller Pages
```
```bash
cat config/routes.rb
```
```result
: Rails.application.routes.draw do
:   root to: "pages#index"
: end
```

8) Add homepage, and React Component
```bash
cat app/views/pages/index.html.erb
```
```result
: <%= react_component("HelloWorld") %>
```

9) Start a Rails server

```bash
$ rails s
```
