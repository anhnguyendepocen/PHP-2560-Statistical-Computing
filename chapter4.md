---
title       : Functions in R
description : In this chapter we will explore creating and debugging functions in R.



--- type:VideoExercise lang:r xp:25 skills:1 key:b330fb454f
## Basic Function Design in R

*** =video_link

//player.vimeo.com/video/184065557




--- type:NormalExercise lang:r xp:100 skills:1 key:e412be26b2
## Basic Functions in R Exercise


We want to start creating functions in R but we need to start out slowly. 

*** =instructions

Write an R function called `welcome`. 

- This function will take no arguments
- When called this function will print out "Welcome to Functions in R!"
- Write this function and then call it. 


*** =hint

Remember the parts of the function. This is very similar to one created during the video.


*** =pre_exercise_code
```{r}

```


*** =sample_code

```{r}
# Write the function welcome


# call the function welcome
```

*** =solution

```{r}
# Write the function welcome

welcome <- function(){
        print("Welcome to Functions in R!")
        }

# call the function welcome

welcome()

```

*** =sct
```{r}
test_function_definition("welcome",
                              body_test = test_function("print", incorrect_msg="Did you call the print function?"))
test_student_typed("Welcome to Functions in R!")
success_msg("Great!")
```





--- type:NormalExercise lang:r xp:100 skills:1 key:0e2f719dab
## Slightly More advanced Functions in R Exercise


We will now make a function that takes some arguments in R. 

*** =instructions

Write a function called `my_abs`.

- This function will take an argument `x`. 
- This function will use `ifelse` function to define output absolute value of `x`.
- Call this function for `c(-2,2)` and name this `out`.


*** =hint

Remember the parts of the function. This is very similar to one created during the video.


*** =pre_exercise_code
```{r}

```


*** =sample_code

```{r}
# Write the function my_abs


# call the function with c(-2,2)
```

*** =solution

```{r}
# Write the function my_abs

my_abs <- function(x){
            ifelse(x>=0, x, -x)
            }
            


# call the function with c(-2,2) name this out

out <- my_abs(c(-2,2))

```

*** =sct
```{r}
test_function_definition("my_abs",
                              function_test= {
                              test_expression_result("my_abs(-1)")
                              test_expression_result("my_abs(1)")
                              }, 
                              body_test = test_function("ifelse", incorrect_msg="Did you use ifelse?"))
test_object("out")
success_msg("Great!")
```




--- type:NormalExercise lang:r xp:100 skills:1 key:abb14a9293
## Functions as Objects in R Exercise


We will now make a function that calls other functions. 

*** =instructions

Write a function called `my_row`.

- This function will take arguments, `mat` and `func`. 
- This function will use the `apply()` function with `mat` as the object and `func` as the function. 
- Make sure this operates on the row.
- Call this functon for `mat=A` and `func=mean`. Name this `out`.


*** =hint

Remember the parts of the function. This is very similar to one created during the video.


*** =pre_exercise_code
```{r}
A = matrix( 
     c(2, 4, 3, 1, 5, 7), # the data elements 
    nrow=2,              # number of rows 
    ncol=3,              # number of columns 
    byrow = TRUE)        # fill matrix by rows
```


*** =sample_code

```{r}
# Write the function my_row


# call the function as directed and name out
```

*** =solution

```{r}
# Write the function my_row

my_row = function(mat,func){
                apply(mat, 1, func)
                }

# call the function as directed and name out
out <- my_row(A, mean)
```

*** =sct
```{r}
test_function_definition("my_row",
                              function_test= {
                              test_expression_result("my_row(A,sum)")
                              test_expression_result("my_row(2*A,mean)")
                              }, 
                              body_test = test_function("apply", incorrect_msg="Did you use apply?"))
test_object("out")
success_msg("Great!")
```

--- type:VideoExercise lang:r xp:25 skills:1 key:e84601da06
## Debugging Functions in R

*** =video_link

//player.vimeo.com/video/184067063



--- type:MultipleChoiceExercise lang:r xp:75 skills: key:2526ff8b47
## Debugging Functions Multiple Choice 


With Debugging we want to make sure we follow some procedures in order to correctly diagnose and repair our functions. 

Answer the following Question:

Which of the following is **NOT** a stage of debugging?

*** =instructions



- Modify the Code.
- Characterize the Error
- Localize the error
- Delete code leading to error.



*** =hint

Remember the stages of debugging

*** =pre_exercise_code
```{r}


```

*** =sct
```{r}

test_mc(correct=4, feedback_msgs = c("Incorrect: We need to modify the code in order to remove the error", 
                                        "Incorrect: This is the first stage, where we try and figure out what is going wrong. ",
                                        "Incorrect: We need to figure out where in the function the error is coming from before modifying.",
                                        "Correct: We should not delete the code but correct it! "))

```









--- type:VideoExercise lang:r xp:25 skills:1 key:3c0bd31c27
## Some Debugging Methods in R

*** =video_link

//player.vimeo.com/video/184080457





--- type:NormalExercise lang:r xp:100 skills:1 key:0f6e468d43
## Debugging Methods in R Exercise

We will begin with some simple debugging methods. 
*** =instructions

Consider the function `my_mean`

- This function does not work on strings. 
- Use the `stopifnot()` function to stop if the value put into this function is a not numeric.  


*** =hint

Figure out how to insert the `stopifnot` in here. How can we test if our value is a string?


*** =pre_exercise_code
```{r}
allow_solution_error()
```


*** =sample_code

```{r}

#Add stopifnot message in so that you do not get an error
# when you use a string

#This function calculates the mean of an object.size
# The object should not be a string
# It outputs the mean
my_mean <- function(x){
            mu <- sum(x)/length(x)
            return(mu)
            }

# If you do this right, you will not get an error here.

out <- my_mean(as.character(2))
                
```

*** =solution

```{r}
#Add stopifnot message in so that you do not get an error
# when you use a string

#This function calculates the mean of an object.size
# The object should not be a string
# It outputs the mean
my_mean <- function(x){
            stopifnot(is.numeric(x))
            mu <- sum(x)/length(x)
            return(mu)
            }

# If you do this right, you will not get an error here.

out <- my_mean(as.character(2))
       
```

*** =sct
```{r}
test_student_typed("stopifnot(is.numeric(x))", not_typed_msg="Make sure you stop if it is not numeric, use is.numeric")
success_msg("Great!")
```

test_e







--- type:VideoExercise lang:r xp:25 skills:1 key:35d2362554
## Designing Programs for Debugging in R

*** =video_link

//player.vimeo.com/video/184133246







--- type:MultipleChoiceExercise lang:r xp:75 skills: key:42f9cfd2af
## Designing Programs for Debugging MC


When we design functions we do not need to work about Procedure as long as we can get the right answer.

*** =instructions

- True
- False


*** =hint

Remember what was said in the video for this. 


*** =pre_exercise_code
```{r}


```

*** =sct
```{r}

test_mc(correct=2, feedback_msgs = c("Incorrect: While the answer is important so is how we arrive at it. ",
                                        "Correct: We need to be mindful how we arrive at an answer! "))

```




--- type:MultipleChoiceExercise lang:r xp:75 skills: key:df820a1cb3
## Designing Programs for Debugging MC #2


Why do we perform cross-checks?

*** =instructions

- Because we are not concerned about the penalty box.
- Because we need ot make sure new versions of code are better than old versions of code.
- Because we have no better method for checking.
- Because we need ot make sure new versions of code are at least as good as an old versions of code.


*** =hint

Remember what was said in the video for this. 


*** =pre_exercise_code
```{r}


```

*** =sct
```{r}

test_mc(correct=4, feedback_msgs = c("Incorrect: This makes sense for hockey but not R.",
                                        "Incorrect: We are not looking for better but to make sure they work as well. ",
                                        "Incorrect: there really is not a ranking order to checks",
                                        "Correct: We need our function to perform as well as the other in certain tests! "))

```



--- type:VideoExercise lang:r xp:25 skills:1 key:b0337a0e75
## Designing Functions in R

*** =video_link

//player.vimeo.com/video/184134719


--- type:VideoExercise lang:r xp:25 skills:1 key:2f6772ef47
## Top Down Function Design in R

*** =video_link

//player.vimeo.com/video/184136056




--- type:MultipleChoiceExercise lang:r xp:75 skills: key:2a36ddd562
## Top Down Function Design MC


When we divide and conquer a good method might be to break up our 300 line code into chunks of 100 lines and work with those blocks.

*** =instructions

- True
- False

*** =hint

There are only 2 choices you really should not ask for a hint!


*** =pre_exercise_code
```{r}


```

*** =sct
```{r}

test_mc(correct=2, feedback_msgs = c("Incorrect: We really need to be concerned with useable chunks not just a specific number of lines.",
                                        
                                        "Correct: Splitting it into 100 lines does not mean we can do something with each 100 line section. We may end up splitting it in the middle of code.  "))

```





--- type:MultipleChoiceExercise lang:r xp:75 skills: key:bb49fc9b2c
## Top Down Function Design MC #2


Which of the following is **NOT** a correct statement about when top down design works.

*** =instructions

- A systematic way to solve the problem.
- The entire problem. 
- An efficient way to solve the problem.

*** =hint

You should not need hints on multiple choice. 


*** =pre_exercise_code
```{r}


```

*** =sct
```{r}

test_mc(correct=3, feedback_msgs = c("Incorrect: We really need to have a systematic method which we can follow to solve this.  ",
                                        
                                        "Inorrect: You cannot perform a top down design if you do not understand the problem.  ", 
                                        "Correct: You may not know how to achieve efficiency (or fast code) however you can still approach it from an algorithmic standpoint and top down design it."))

```



--- type:VideoExercise lang:r xp:25 skills:1 key:5fc6a5dbb8
## Refactoring Functions in R

*** =video_link

//player.vimeo.com/video/184136884




--- type:MultipleChoiceExercise lang:r xp:75 skills: key:6a830662f7
## Refactoring MC


What do we do in refactoring?

*** =instructions

- Group Related values into objects. 
- Common tasks become shared functions.
- Common overall tasks become general functions.
- Factor out code in order to split it up. 
- Give transparent names.

*** =hint

You should not need hints on multiple choice. 


*** =pre_exercise_code
```{r}


```

*** =sct
```{r}

test_mc(correct=4, feedback_msgs = c("Incorrect: This is part of the process.  ",
                                        
                                        "Incorrect: This is part of the process.  ", 
                                        "Incorrect: This is part of the process.  ", 
                                        "Correct: We are not really looking to split up coding but to make it more concise.",
                                        "Incorrect: This is part of the process.  "))

```

