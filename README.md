# Ex.05 Design a Website for Server Side Processing
# Date: 22-4-2025
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM : 
```
filename.html
<html>
<head>
    <title>power</title>
    </head>
<body>
    <h1 align="center" > power calculator</h1>
    <form align="center" method="POST">
    {%csrf_token%}
     
    <div class="power">

        <label for="INTENSITY"><b>INTENSITY:</b></label>
        <input type="text" name="intensity" id="INTENSITY" placeholder="Enter the Value" value="{{i}}">
    </div>
    <br>
    <div class="power">
        <label for="RESISTANCE"><b>RESISTANCE:</b></label>
        <input type="text" name="resistance" id="RESISTANCE" placeholder="Enter the Value" value="{{r}}">
    </div>
    <br>
    <input type="submit" value="CALCULATE">
    <br>
    <br>
    <div class="power">
        <label for="POWER"><b>POWER:</b></label>
        <input type="text" name="POWER" id="POWER" placeholder="Answer" value="{{power}}">
        
    </div>
</form>
</body>
</html>
views.py
rom django.shortcuts import render
def powerlamp(request): 
    context={} 
    context['power']="0" 
    context['i']="0" 
    context['r']="0" 
    if request.method=='POST': 
        print("POST method is used")
        i=request.POST.get('intensity','0')
        r=request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',i) 
        print('resistance=',r) 
        power=(int(i) ** 2 ) * int(r) 
        context['power']=power
        context['i']=i
        context['r']=r 
        print('Power=',power) 
    return render(request,'mathapp/filename.html',context)
    urls.py
    from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('powerlamp/',views.powerlamp,name="powerlamp"),
    path('',views.powerlamp,name="powerlamproot")

]

```
# SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-04-08 115209.png>)
# HOMEPAGE:
![alt text](<Screenshot 2025-04-22 110542.png>)
# RESULT:
The program for performing server side processing is completed successfully.
