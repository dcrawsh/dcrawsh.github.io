---
layout: post
title:      "Riding the rails with Casey Jones"
date:       2020-02-25 23:51:16 +0000
permalink:  riding_the_rails_with_casey_jones
---


-Some thoughts and discussion on using Active Storage in your Rails Application

For my project I created a niche version of Craiglist. The 2 qualifying unique characteristics are that it is only for the selling and buying of musical instruments/equipment and the other is that it is only for the Greater Portland, Oregon area. 

According to The Rails Guide. **Active Storage** "facilitates uploading files to a cloud storage service like Amazon S3, Google Cloud Storage, or Microsoft Azure Storage and attaching those files to Active Record objects. It comes with a local disk-based service for development and testing and supports mirroring files to subordinate services for backups and migrations."

For my uses I wanted to allow Users to upload picutes of the items they were selling.  As my app is in development I used local disk-based service.

Setup: Declare Active Storage services in config/storage.yml

``local:
  service: Disk
  root: <%= Rails.root.join("storage") %>``

add the following to config/environments/development.rb
``config.active_storage.service = :local``

and declare a Disk service in config/storage.yml
``local:
  service: Disk
  root: <%= Rails.root.join("storage") %>``
	
	Next I needed to attach files to records so in the User model
	
	``class User < ApplicationRecord
  has_one_attached :image
end``

I then needed to add a field in the view form to add a image and also in the controller update the strong params to include :image.


