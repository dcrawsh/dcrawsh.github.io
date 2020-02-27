---
layout: post
title:      "Has many through, a relationship story"
date:       2020-02-27 22:33:19 +0000
permalink:  has_many_through_a_relationship_story
---


A quick primer on the two most basic of model associations. 

**belongs_to** association is a 1:1 connection with another model.  For example each instance of the model belongs to one instance of another model.  If your application includes chefs and recipes; each recipe can be assigned to exactly one author.  the model would look like:

model
``class Recipe < ApplicationRecord
  belongs_to :chef
end``

migration
``class CreateRecipes < ActiveRecord::Migration[5.0]
  def change
    create_table :chefs do |t|
      t.string :name
      t.timestamps
    end
 
    create_table :books do |t|
      t.belongs_to :author
      t.datetime :published_at
      t.timestamps
    end
  end
end``

**has_many** association is a 1:many connection with another model. This is the other side of a belongs_to association and indicates that each instance of the model has many instances of another model.  In an application containing chefs and recipes, the cheft model would look like:

``class Chef < ApplicationRecord
  has_many :recipes
end``

migration
``class CreateChefs < ActiveRecord::Migration[5.0]
  def change
    create_table :chefs do |t|
      t.string :name
      t.timestamps
    end
 
    create_table :recipes do |t|
      t.belongs_to :chefs
      t.datetime :published_at
      t.timestamps
    end
  end
end``

*and finally...*

**has_many :through** association is a many:many connection with another model.  What this essentially means is that the model can be matched with many instances of another model by looking into the attributes of a third model. For example, consider a restaurant where **customers** order **meals** to be made by **chefs**. The models would look like this: 

class Chef < ApplicationRecord
  has_many :meals
  has_many :customers, through: :meals
end
 
class Meal < ApplicationRecord
  belongs_to :chef
  belongs_to :customer
end
 
class Customer < ApplicationRecord
  has_many :meals
  has_many :chefs, through: :meals
end

The :through option added to the has_many association simply designates a join model through which to perform the query.  The join model therefore belongs to both models which are desired to have the has_many :through relationship.  Therefore, the join table will have a foreign key for both models it is connecting.





