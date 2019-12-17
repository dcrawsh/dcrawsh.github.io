---
layout: post
title:      "Fly Me Too the Moon"
date:       2019-12-17 14:27:10 -0500
permalink:  fly_me_too_the_moon
---

![](https://i0.wp.com/mannequintheband.com/wp-content/uploads/2015/04/frank-sinatra-fly-me-to-the-moon-1.jpg?resize=300%2C300

My Sinatatra project was a success. But inital setup can be difficult as not too many people seem to actually use Sinatra with the existance and power of Rails. At the end of my project I had created 7 controllers and 5 different models. I am excited to see the power of Rails in action in helping with that burden of work.  One of the most difficult aspects was creating the joining model of my Employees and Trainings. This model I named Employtrains and it worked to match a training with an employee and add a date. Below is the code and how to create such a relationship.

```class Employee < ActiveRecord::Base 
    belongs_to :site
    has_many :employtrains
    has_many :trainings, through: :employtrains
    validates :workdayid, uniqueness: true 
end```

*Disregard the belongs to for this pupose. But the employee has a "has_many" relationship with the joining model. It also has a "has_many through" relationship to trainings through employtrains.

```class Training < ActiveRecord::Base 
  has_many :employtrains
  has_many :employees, through: :employtrains
end```

*Training has a "has_many" relationship with the joining model. It also has a "has_many through" relationship to Employees through employtrains.


```class Employtrain < ActiveRecord::Base 
    belongs_to :employee 
    belongs_to :training
end```

*Employtrain "belongs_to" both models that it is joing and therefore active record creates a foreign key for each of those models inside Employtrain. I can then add a date attribute to Emplytrain to mark the date that a particular employee completed a particular training





