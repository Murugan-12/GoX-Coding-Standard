# Coding Conventions
Coding conventions secure quality, code readabilty and make code maintanence easier   

# Rules of JavaScript

## 1.Magic Numbers

>
> Assiging a number with no meaning
> for example: for(let i=0;i<86400;i++) where 86400 means nothing
> 
> To make it easier to read we can use **const SECONDS_IN_A_DAY = 86400**


## 2.Deep Nesting

>
> const exampleArr = [ [ ['value'] ] ]  
> To retrieve the value we will be doing nested for loops  
> for example: exampleArr.forEach((arr1)=>{ arr1.foreach((arr2)=>{ arr2.foreach((element)=> return element ) }) })  
>
> Instead of reusing the code several times we can create a recusive function   
> for example: const retrieveValue = (element) => {   
>   if(Array.isarray(element)){ retrieveValue(element) }  
>   return element  
> }  
> retrieveValue(exampleArr)


## 3.Stop writing comments

>
> Its a little bit subjective topic but when you write a program which is self explanatory, the whole program will look clean and 
> it will be really helpful for others to understand code as it improves readability


## 4.Avoid large functions

>
> For example: const arithmeticOperations = (a,b,c) => {  
> const addition = a + b + c;  
> const subtraction = a - b - c;  
> const multiplication = a * b * c;  
> return { addition, subtraction, multiplication}  
> }  
>
> In above example we are calling a function we does mupltiple operations, as we took simple example the code looks easy to understand but
> in real time projects we will be dealing with too many operations in that case we can allocate functions for each opeartion and call
> wherever we want.
>
> For example: const arithmeticOperations = (a,b,c) => {  
> return { addition(), subtraction(), multiplication()}  
> }  
> 
> const addition = (a,b,c) => return {a + b + c};  
> const subtraction = (a,b,c) => return {a - b - c};  
> const multiplication = (a,b,c) => return {a * b * c};  