# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
Clone the repository from Github

### Step 2:
Create Django admin project.

### Step 3:
Create a new app.

### Step 4:
Create python programs for views and urls.

### Step 5:
Create a HTML file of forms

### Step 6:
Publish the website in the given URL.


## PROGRAM :
```

math.html

<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of Triangle</title>   
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style>
body {
background-color:orange;    
}
.edge {
width: 1080px;
margin-left: auto;
margin-right: auto;
padding-top: 200px;
padding-left: 300px;    
}
.box {
display:block;
border: Thick dashed lime;
width: 500px;
min-height: 300px;
font-size: 20px;
background-color:dark green;    
}
.formelt {
color:Red;
text-align: center;
margin-top: 5px;
margin-bottom: 5px;    
}
h1{
color: blue;
text-align: center;
padding-top: 20px;    
}
</style> 
</head>    
<body>
<div class="edge">
<div class="box">
<h1>Area of a Triangle</h1> 
<form method="POST">
{% csrf_token %}
<div class="formelt">
Height : <input type="text" name="height" value="{{h}}"></input>(in m)<br/>
</div>
<div class="formelt">
Base : <input type="text" name="base" value="{{b}}"></input>(in m)<br/>    
</div>    
<div class="formelt">
<input type="submit" value="Calculate"></input><br/>    
</div>
<div class="formelt">
Area : <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>    
</div>
</form>   
</div>    
</div>
</body>
</html>

views.py

from django.shortcuts import render
def trianglearea(request):
    context={}
    context['area'] = "0"
    context['h'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        h = request.POST.get('height','0')
        b = request.POST.get('base','0')
        print('request=',request)
        print('height=',h)
        print('base=',b)
        area = int(h) * int(b)/2
        context['area'] = area
        context['h'] = h
        context['b'] = b
        print('Area=',area)
    return render(request,'myapp/math.html',context) 

urls.py

from django.contrib import admin
from django.urls import path
from myapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaoftriangle/',views.trianglearea,name="areaoftriangle"),
    path('',views.trianglearea,name="areaoftriangleroot")
]

```

## OUTPUT:
![image](https://github.com/KameshLeVI/serversideprocessing/assets/120780633/b9b9a172-3c71-4def-834f-f2e63ab1b8ca)


### Home Page:
![exp 5 ](https://github.com/KameshLeVI/serversideprocessing/assets/120780633/1eb1336a-652c-4d78-8807-44bf825fc51a)


## Result:
The program for implementing server side processing completed successfully.

