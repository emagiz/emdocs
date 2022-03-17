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

# Actualize properties

In this microlearning, we will focus on the situation where an existing property needs a change of its value and how to put this value into effect in your environment. This microlearning is specifically created for Generation 3 runtime environments

Should you have any questions, please contact academy@emagiz.com.

- Last update: March 17th, 2022
- Required reading time: 3 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform
- Understanding of property concept
- At least one flow for which you can change the actual and where that flow is active
- An integration model that has 1 or more runtimes that are running on the Generation3 version runtime

## 2. Key concepts
Changing the value of any property is rather easy, yet the value is not taken into account by the flow before that flow is restarted properly due to the nature in which eMagiz is using Java.

##### Theory

## 3. Actualize properties

### 3.1 Update properties for Generation 2 runtimes

Below are the steps to take to change the value of a property and putting that into effect.

1. Locate the property via the access points for properties (refer to the Properties Management microlearning)
2. Change the value of the property and press save
3. Locate the Runtime dashboard and find the flow for which the property has changed
4. Ensure the properly stop and start the flow

**Considerations**
- Starting and stopping flows can be done in direct sequence, unless you change the property of that particular flow multiple times within 2 minutes. eMagiz needs in that case 2 minutes to store the property value properly.

### 3.2 Update properties for Generation 3 runtimes

Below are the steps to take to change the value of a property and putting that into effect. Please note that the properties are stored inside the docker image of the runtime, and that the action Set release as active means create a new docker image.

1. Locate the property via the access points for properties (refer to the Properties Management microlearning)
2. Change the value of the property and press save
3. Create a new release for the environment where that property needs to be effectuated
4. Set the release as active, and ensure the runtimes are deployed afterwards (via Deployment Plan or Deploy Architecture).

##### Practice

## 4. Assignment

Add one property via the property overview and subsequently edit this property via the Properties TAP overview. Link another property with the help of the Set release properties functionality (with the help of the Check properties option) and deploy this release. This assignment can be completed within the Deploy phase of your (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Make a good plan before you change the property so that there are no unforeseen side effects
- For Generation 2 runtimes, in case the value is changed several times, the flow will need 2 minutes of breathing time before the updated property value is taken into account.
- For Generation 3 runtimes, a new release is required to effectuate the property.

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help text provided by eMagiz when executing these actions.

## 7. Silent demonstration video

This video demonstrates how you could have handled the assignment and gives you some context on what you have just learned.

<iframe width="1280" height="720" src="../../vid/microlearning/crashcourse-platform-deploy-property-management.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</div>
</main>
</div>
</div>