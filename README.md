# Ex.05 Design a Website for Server Side Processing
## Date:30/9/2025
## AIM:
 To desgin a website to calculate the body mass index(BMI)in the server 


## FORMULA:
BMI = W/(H/100)<sup>2</sup>
<br> BMI --> Body Mass Index
<br> W --> weight
<br> H --> height

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
        <title>CALCULATE BMI </title>
    <style>
        body{
            font-family:Arial,sans-serif;
            background-color:rgb(68, 0, 255);
            color:white;
            display:flex;
            justify-content: center;
            align-items: center;
            height:100vh;
            border-radius: 5%;
            background: rgb(240, 4, 28);

        }
         body {
            font-family: Arial, sans-serif;
            margin: 45px;
            background-color: rgb(6, 251, 222);
        }
        form {

            padding: 20px;
            border-radius: 8px;
            width: 300px;
        }
        input {
            margin-top: 10px;
            width: 100%;
            padding: 8px;
        }
        h2 {
            margin-top: 20px;
        }
        .container {
            background-color: rgb(0, 0, 0);
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-style: dashed;
        }
   </style>
</head>
<body>
    <center>
    <div class="container">
        <div class="goku">
                <h1>BMI CALCULATER</h1>
                <h1>S.DEEPAKKUMAR(25016457)</h1>
    <form method="post">
        {% csrf_token %}
        <label for="height">HEIGHT [cm]:</label>
        <input type="text" id="height" name="height" required>

        <label for="weight">WEIGHT [kg]:</label>
        <input type="text" id="weight" name="weight" required>

        <input type="submit" value="CALCULATE_BMI">
    </form>

    {% if bmi %}
        <h2>YOUR BMI: {{ bmi }}</h2>
        {% if category %}
            <p>Category: {{ category }}</p>
        {% endif %}
    {% endif %}
        </div>
    </div>
    </center>
</body>
</html>


urls.py

from django.contrib import admin
from django.urls import path
from myapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('bmi/', views.calculate_bmi, name="bmi"),
    path('', views.calculate_bmi, name="bmicalculator"),
]


views.py

from django.shortcuts import render
def calculate_bmi(request):
    context={}
    context['bmi']="0"
    context['w']="0"
    context['h']="0"
    if(request.method=='POST'):
       w= float(request.POST.get('weight','0'))
       h=float(request.POST.get('height','0'))
       print('request=',request)
       
       print('Weight=',w)
       print('Height=',h)
       bmi=w/((h/100)**2)
       context['bmi']=bmi
       context['w']=w
       context['h']=h
       print('BMI=',bmi)
    return render(request,'myapp/math.html',context)
```




## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-10-01 192826.png>)


## HOMEPAGE:
![alt text](<Screenshot 2025-10-01 192758.png>)


## RESULT:
The program for performing server side processing is completed successful