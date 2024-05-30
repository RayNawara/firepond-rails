# README

Filepond-rails

https://github.com/Code-With-Rails/filepond-rails

rails new (with importmap)

then:
```
rails active_storage:install
rails db:migrate
```
Add this line to your application's Gemfile:
```
gem 'filepond-rails'
```
Also uncomment image_processing!

And then run:
```
bundle
```
Add the following to your application.css:
```
*= require 'filepond'
```
Add javascript_importmap_tags in the head section of your layout:
```
<%= javascript_importmap_tags %>
```
Then run
```
importmap pin @rails/activestorage
```
Mount filepond-rails routes:
```ruby
Rails.application.routes.draw do
  mount Filepond::Rails::Engine, at: '/filepond'
end
```
The gem assumes that you set up your models and Active Storage configuration in a standard Rails way. Assuming you have a form that looks like this:
```ruby
<%= form_with model: @user, url: update_avatar_path, method: :post do |f| %>
  <%= f.label :avatar, 'Update your avatar' %>
  <%= f.file_field :avatar, class: 'filepond', direct_upload: true %>
  <%= f.button 'Update' %>
<% end %>
You can instantiate the file_field component like so:
```
```
// app/javascript/application.js
import { FilePondRails, FilePond } from 'filepond-rails'

window.FilePond = FilePond
window.FilePondRails = FilePondRails

const input = document.querySelector('.filepond')
FilePondRails.create(input)
```
