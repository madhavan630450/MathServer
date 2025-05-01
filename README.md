# Ex.05 Design a Website for Server Side Processing
## Date:01.05.25
## Name:MARIMUTHU MATHAVAN
## Reg no:212224230153

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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
<!DOCTYPE html>
<html>
<head>
    <title>POWER OF LAMP</title>
    <style>
        body {
            background-color: rgb(213, 11, 210);
            text-align: center;
            margin-top: 100px;
        }
        .container {
            display: inline-block;
            padding: 30px;
            background-color: white;
            border: 3px dashed black;
        }
        input[type="text"] {
            width: 200px;
            padding: 5px;
            margin: 5px;
        }
    </style>
</head>
<body>

<div class="container">
    <h3>MARIMUTHU MATHAVAN (212224230153)</h3>
    <h1><b>POWER OF LAMP</b></h1>

    <form method="POST">
        {% csrf_token %}

        <label>Intensity (I):</label>
        <input type="text" name="intensity" placeholder="Enter Intensity"> (in Amperes) <br><br>

        <label>Resistance (R):</label>
        <input type="text" name="resistance" placeholder="Enter Resistance"> (in Ohms) <br><br>

        <button type="submit">Calculate</button> <br><br>

        <label>Power (P):</label>
        <input type="text" readonly value="{{ powerlamp }}"> (in Watts)
    </form>

</div>

</body>
</html>

views.py
from django.shortcuts import render

def power(request):
    context = {'powerlamp': ""}

    if request.method == "POST":
        i = request.POST.get('intensity', '')
        r = request.POST.get('resistance', '')

        if i and r:
            try:
                i = float(i)
                r = float(r)
                p = (i ** 2) * r
                context['powerlamp'] = round(p, 2)  
            except ValueError:
                context['powerlamp'] = "Invalid input"

    return render(request, 'mathapp/math.html', context)

urls.py
from django.contrib import admin
from django.urls import path
from mathapp import views   # Import your app5 views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.power, name='power'),  # Home page will open the lamp power calculator
]
```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-05-01 221445.png>)

## HOMEPAGE:
![alt text](<Screenshot 2025-05-01 221323.png>)



## RESULT:
The program for performing server side processing is completed successfully.
