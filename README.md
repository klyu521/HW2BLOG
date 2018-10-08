# HW2BLOG
## Homework 

### Step 1:Create new folders and a new branch.
```
mkdir hw2
cd hw2
git checkout -b hw2
git branch
```

###  Step 2: Design my projeect
I want to design a web calulator and I do a lot of researches about how to make a calulator. First I make the part of html.
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Calulator</title>
     <link rel='stylesheet' href='https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css'>
    <link rel="stylesheet" type="text/css" href="style.css">
  <script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
</head>
<body>
<div id="calculator">
    <div id="screen">
        <p id="txt1"></p>
        <p id="txt2"></p>
    </div>
    <div id="workspace">
        <div id="num">
            <input type="button" value="7">
            <input type="button" value="8">
            <input type="button" value="9">
            <input type="button" value="4">
            <input type="button" value="5">
            <input type="button" value="6">
            <input type="button" value="1">
            <input type="button" value="2">
            <input type="button" value="3">
            <input type="button" value="C">
            <input type="button" value="0">
            <input type="button" value=".">

        </div>
        <div id="operator">
            <input type="button" value="+">
            <input type="button" value="-">
            <input type="button" value="*">
            <input type="button" value="/">
            <input type="button" value="=">
        </div>


    </div>
</div>
```
Next I make the CSS file to make my web more beautiful, and it reference to some web calulators.
```
<style>
    *{
        margin: 0;
        padding: 0;
    }
    #calculator{
        margin: 50px auto;
        padding: 5px;
        width: 230px;
        height: 230px;
        background: rgb(190,210,224);
    }
    #screen{
        width: 230px;
        height: 60px;
        background: rgb(153,153,153);
        border-radius: 5px;
        text-align: right;
        overflow: hidden;
    }
    #txt1{
        height: 20px;
        padding-top: 10px;
        font-size: 10px;
    }
    #txt2{
        height: 30px;
        font-size: 20px;
    }
    #num{
        float:left;
        width: 130px;
    }
    #num input{
        width: 40px;
        height: 40px;
        margin-top: 3px;
    }
    #operator{
        float:right;
        width: 70px;
        height: 170px;
    }
    #operator input{
        width: 70px;
        height: 30px;
        margin-top: 4px ;
    }
    #converter{
        float:right;
        width: 70px;
        height: 170px;
    }
    ```
    
    ###Last it is the part of javascript and jQuery.
    
    ```
    <script type="text/javascript">
    $(function(){
         var i=0;//i is clear signal
        //get input number
        $("#num input").click(function () {
           //Judge whether the result of the last calculation is saved in #txt2, if it is, then empty it.
            if (i===1){
                $("#txt2").text("");
                }
            //make sure number is displayed in the correct format
            //Implementation using switch statement
            switch ($(this).val()){
                 case "C":
                     $("#txt2").text("");
                     break;
                 case ".":
                     if ($("#txt2").text().indexOf(".") != -1) {
                     break;
                     }else{$("#txt2").append($(this).val());}
                      break;
                 default:
                      if ($("#txt2").text() === "0") {
                          $("#txt2").text($(this).val());
                        }else{
                           $("#txt2").append($(this).val());
                        }
                   }

                  i=0;
         });
        //Get operator
         $("#operator input:not(:last)").click(function () {
             $("#txt1").text($("#txt2").text()+$(this).val());
             $("#txt2").text("");
         });
         //click "=" to calulate
         $("#operator input").last().click(function () {


             var str=$("#txt1").text();
             var n1=parseFloat(str);
             var n2=parseFloat($("#txt2").text());
             var cal=str[str.length-1];
             switch (cal){
                 case "+":
                     $("#txt2").text( n1+n2);
                     break;
                 case "-":
                     $("#txt2").text( n1-n2);
                     break;
                 case "*":
                     $("#txt2").text( n1*n2);
                     break;
                 case "/":
                     $("#txt2").text( n1/n2);
                     break;
                 default: break;
             }
             $("#txt1").text( "");
             i=1;
         });
    });
</script>
```


### Step 3: Merge branch to master
```
git all *
git commit -m "hw2"
git push -u origin hw2
git checkout master
git merge hw2
git push -u origin master
```

    
