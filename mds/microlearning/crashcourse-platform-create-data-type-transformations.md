<div class="ez-academy">
	<div class="ez-academy__body">
		<main class="micro-learning">
		<ul class="doc-nav">
			<li class="doc-nav__item"><a href="../../docs/microlearning/crashcourse-platform-index" class="doc-nav__link">Home</a></li>
			<li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
			<li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
			<li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
			<li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
		</ul>

<div class="doc">

##### Intro

# Data type transformations
The data type (i.e. string, dateTime, boolean, integer, or decimal) of attributes can differ between the input definition and the target definition.
To ensure that you end up with a valid target message you will need a data type transformation to reach that goal.

In this microlearning, we will educate you on the possibility of data transformations in eMagiz.

Should you have any questions, please contact academy@emagiz.com.

- Last update: February 9th, 2021
- Required reading time: 3 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning focuses on data type transformations.

With data type transformations we mean: Ensuring that the output is valid according to the data type of the attribute in the target message

##### Theory

## 3. Data type transformations
Several data type transformations could be done with eMagiz. In this microlearning, we will focus on the one that you will use the most.
Transforming from a string to a date(Time). To illustrate this point I made a new mapping in Design, this time one for an API Gateway flow.

<p align="center"><img src="../../img/microlearning/crashcourse-platform-create-data-type-transformations--data-type-transformation-starting-point.png"></p>

As we talk about a transformation we need to select the transformation icon (the blue rectangle, remember). This will lead us to the following pop-up

<p align="center"><img src="../../img/microlearning/crashcourse-platform-create-data-type-transformations--data-type-transformation-pop-up.png"></p>

In this pop-up, we have the option to convert the datatype. As the name suggests, this is the option we want to use this time

<p align="center"><img src="../../img/microlearning/crashcourse-platform-create-data-type-transformations--data-type-transformation-pop-up-convert-datatype.png"></p>

Now the only thing we need to know is how (in which notation) the backend operation of our API Gateway will return the Datum. 

In this case, the dates they return are formatted as dd-MM-yyyy. So let's alter the input format in eMagiz to represent that.

<p align="center"><img src="../../img/microlearning/crashcourse-platform-create-data-type-transformations--data-type-transformation-pop-up-convert-datatype-filled-in.png"></p>

Save your solution and you will notice that the warning is gone from eMagiz as you have successfully transformed the content of Datum to a valid date.

So, remember to check for the option convert datatype when you have a mismatch in the datatype between input and output.

##### Practice

## 4. Assignment

Use the convert datatype option to transform an input string in the format dd/MM/yyyy to a valid date in one of the transformations in your project. 
If you do not have one available you can add another integration via Capture, Design, and Create to access the transformation.
This assignment can be completed within the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Data type transformation is to ensure that the output is valid according to the underlying rules of that data type
- eMagiz gives you the option to convert the datatype in most cases via the visual tooling
- Without knowing the input format it will be impossible to make a successful data type transformation

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help text provided by eMagiz.

## 7. Silent demonstration video

This video demonstrates a working solution and how you can validate whether you have successfully completed the assignment.

<iframe width="1280" height="720" src="../../vid/microlearning/crashcourse-platform-create-data-type-transformations.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</div>
</main>
</div>
</div>