---
layout: post
title:      "JS - Project NYC PupPals"
date:       2020-08-04 19:59:47 -0400
permalink:  js_-_project_nyc_puppals
---


For my JS project i decided to take on my biggest undertaking yet. I recently got a puppy that is cute as her little heart shaped nose. 
![](https://scontent-lga3-1.cdninstagram.com/v/t51.2885-15/sh0.08/e35/s640x640/106370070_3458092857547708_2840969579228741627_n.jpg?_nc_ht=scontent-lga3-1.cdninstagram.com&_nc_cat=104&_nc_ohc=yXjnKsVIY2EAX_Pngfn&oh=2ce17add6afc41817a303ef9b4f315ce&oe=5F51FE44)
Anyone who gets a puppy always imagines their dog being the best trained dog that will be smart obedient and most importantly, friendly. While you can train your puppy in a multitude of ways the only way to be sure he or she is friendly is to introduce them at a young age to a lot of people and a lot of other dogs. With all this in mind I decided to make what I best describe as tinder for dogs.

The basic run down of the web-app is you as a user have a profile, you can upload a photo of your puppy and all its information. You can then see other people pages one at a time and either give them a thumbs up or down. If you give another user a thumbs up you are now a "follower" of that user. What does it mean to be a follower of a user?

This bring us to our join table. Unlike most join tables this is a self referential table. Self referential table means it joins to of the same models, in this case it joins users with users. Users have many follows and follow many users. 

Join Table:
```
class CreateFollows < ActiveRecord::Migration[6.0]
  def change
    create_table :follows do |t|
      t.timestamps
      t.belongs_to :user
      t.belongs_to :followed_user
      t.index [:user_id, :followed_user_id], unique: true
    end
  end
end
```

The next step is to creat the assosiation in our user class. 

```
  has_many :follows
  has_many :followed_users, through: :follows

  has_many :followers, foreign_key: :followed_user_id, class_name: 'Follow'
  has_many :follower_users, through: :followers, source: :user
```

Finally our follow model:

```
  belongs_to :user
  belongs_to :followed_user, class_name: 'User'
```

Once our relationships are set up we can now call methods like user.follower_users to see who follows the user or user.followed_users to see who the user follows.

Feel free to check out the backend code on my github here:

https://github.com/mattenbar/PupPals_backend



and the front end here: 

https://github.com/mattenbar/PupPals_frontend


