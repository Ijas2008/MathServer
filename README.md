# Ex.05 Design a Website for Server Side Processing
## Date:07.10.2025

## AIM:

 To design a website to calculate the body mass index(BMI) 


## FORMULA:
```
BMI = W/(H/100**2)
BMI --> Body Mass Index 
W --> Weight
H --> Height

```

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
math.html

<html>
  <head>
   <title>Body Mass Index</title>
   <style type="text/css">
body
{
  background-color:cyan;
}
.edge{
width:50%;
margin-left:auto;
margin-right:50%;
padding-top:100px;
padding-left:500px;    
}
.box{
display:block;
border:Thick dashed black;
width:500px;
min-height:300px;
font-size:20px;
background-color:white;    
}
.formelt{
    color:red;
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}
h2
{
color:rgba(0, 0, 0, 1);
text-align:center;
padding-top: 10px;
papping-bottom: 50px;
}
h1{
  color:red;
  text-align:center;
  padding-top: 50px;
} 
    </style>
 </head>
 <body>
   <h1>EX:01-BMI CALCULATOR [Ijas (25007615)]</h1>
  <div class="edge">
    <div class="box">
    <h2>Body Mass Index (BMI) Calculator</h2>
  <form method="POST">
    {% csrf_token %}
  <div class="formelt">
    Weight: <input type="text" name="weight" value="{{w}}"></input>(in kg)<br/>
  </div>
  <div class="formelt">
    Height: <input type="text" name="height" value="{{h}}"></input>(in m)<br/>
  </div>
  <div class="formelt">
    <input type="submit" value="Calculate"></input><br/>
  </div>
  <div class="formelt">
    BMI:<input type="text" name="bmi" value="{{bmi}}"></input>kg/m<sup>2</sup><br/>
  </div>
  </form> 
  </div>
  </div>
 </body>
</html>

view.py

from django.shortcuts import render
def bmi(request):
    context={}
    context['bmi']= "0"
    context['w'] = "0"
    context['h']= "0"
    if request.method == 'POST':
        print("POST method is used")
        w = request.POST.get("weight",'0')
        h= request.POST.get("height",'0')
        print('requestt=',request)
        print('Weight=',w)
        print('Height=',h)
        a=float(w)
        b=float(h)
        bmi = a/(b*b)
        context['bmi']=bmi
        context['w']=w
        context['h']=h
        print('BMI=',bmi)
return render(request,'mathapp/math.html',context)

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('bodymassindex/',views.bmi,name="bodymassindex"),
    path('',views.bmi,name="bodymassindexroot")
]

```

## SERVER SIDE PROCESSING:

![alt text](<ijas/mathapp/Screenshot 2025-10-07 103118.png>)

## HOMEPAGE:

![alt text](<ijas/mathapp/Screenshot 2025-10-07 103041.png>)

## RESULT:
The program for performing server side processing is completed successfully.
