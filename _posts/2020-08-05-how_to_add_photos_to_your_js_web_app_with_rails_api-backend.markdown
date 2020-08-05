---
layout: post
title:      "How to add Photos to your JS web app with Rails Api-Backend"
date:       2020-08-05 08:26:12 -0400
permalink:  how_to_add_photos_to_your_js_web_app_with_rails_api-backend
---


During my Javascript project NYC PupPals I em**BARK**ed on a journey that involved photo uploading... see what i did there?

I had a semi tough time figuring out how to use Cloudinary for photo uploading. If you dont know what cloudinary is check out their site https://cloudinary.com/. 

Here is a brief description from the site explaining what cloudindary is:

"*Cloudinary is an end-to-end image- and video-management solution for websites and mobile apps, covering everything from image and video uploads, storage, manipulations, optimizations to delivery.

*With Cloudinary, you can easily upload images and videos to the cloud and automate smart manipulations of those media without installing any other software. Cloudinary then seamlessly delivers your media through a fast content delivery network (CDN), optimized with the industry’s best practices*.

*Additionally, Cloudinary offers comprehensive APIs and administration capabilities, which you can easily integrate with your web and mobile apps.*"

Below i will show the steps and code I used to allow for user uploading. First step is to set up your free cloudinary account.

When signing up thhe most important parts are creating your cloudname and if you would like to allow users to upload their own photos check the box labeled "**Enabled unsigned uploads**" this allows users to upload their own images.

Once your account is set up, in the back end add **gem 'cloudinary'** to your gem file. Run bundle to install the gem.

Once installed on your cloudinary dashboard download the YML file (found in upper right hand of your dashboard) and add it to your backend config file.

![](https://drive.google.com/file/d/1hAZtdBJpwmILDbKb1FRNU1aq3YBILUKd/view?usp=sharing)

With most of your back end set up lets jump to the front end a little.
First step is to add a form for photo uploading.

```
 <form id="edit-img-form" class="form" action="">
  <label for="img">Select image:</label>
  <input type="file" id="img" name="img" accept="image/*" >
  <br><br>
  <input type="submit" id="imgUploadButton" class="btn btn-info btn-md" value="Save Image">
  </form>
```

once your form is set up get the submit button and add an event listener

```
const imgUploadButton = document.getElementById("imgUploadButton")
imgUploadButton.addEventListener("click", function(e){ 
   imgUploadHandler(e)
 })
```

Finally for the front-end the function that handles the image uploading.

```
function imgUploadHandler(e){
  e.preventDefault()
  const body = new FormData()
  const newImg = document.querySelector("#img").files[0]
  body.append('file', newImg)
  body.append('user_id', state.user.id)
  fetch("http://localhost:3000/api/v1/img-upload",{
    method: "PUT",
    body
  })
}
```

The function uses a fetch request to to send the "body" which contains our image to the back end.

Are you still with me? We are almost there!

The last step on the back-end side is to create the action in your controller that the photos will go to.
(dont forget to also set up the route to this controller)

```
def img_upload
    user = User.find(params[:user_id])
    file_url = Cloudinary::Uploader.upload(params[:file], options = {})
    user.img = file_url["url"]
    user.save
    render json: user
  end
```

Using cloudinary's method `Cloudinary::Uploader.upload(params[:file], options = {})` you now have acccess to (from the gem). The photo gets uploaded to their cloud based server and returns to you a URL for the photo that can be stored as an attribute on your user model.

You can view the repos to my project here: https://github.com/mattenbar/PupPals_frontend

and the back end here: https://github.com/mattenbar/PupPals_backend
