# Actualize properties

In this microlearning we will focus on situation where a existing property needs a change of value and how to put this value into effect in your environmemt.

Should you have any questions, please contact academy@emagiz.com.

- Last update: February 7th 2021
- Required reading time: 3 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform
- Understanding of property concept
- At least one flow for which you can change the actual and where that flow is active

## 2. Key concepts
Changing the value of any property is rather easy, yet the value is not taken into account by the flow before that flow is restarted properly due to the nature in which eMagiz is using Java.

## 3. Actualize properties

Below are the steps to take to change the value of a property and putting that into effect.

1. Locate the property via of the access points for properties (refer to the Properties Management microlearning)
2. Change the value of the property and press save
3. Locate the Runtime dashboard and find the flow for which the property has changed
4. Ensure the properly stop and start the flow

**Considerations**
- Starting and stopping flows can be done in direct sequence, unless you change the property of that particular flow multiple times within 2 minutes. eMagiz needs in that case 2 minutes to store the propertly value properly.


## 4. Assignment

Add one property via the property overview and subsequently edit this property via the Properties TAP overview.
Link another property with the help of the Set release properties functionality (with the help of the Check properties option) and deploy this release.
This assignment can be completed within the Deploy phase of your (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Make a good plan before you change the property so that there are no unforeseen side effects
- In case the value is changed several time, the flow will need 2 minutes breathing time before the updated property value is take into account.

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the helptext provided by eMagiz when executing these actions.

## 7. Silent demonstration video - TO ADD

This video demonstrates how you could have handled the assignment and gives you some context on what you have just learned.

<iframe width="1280" height="720" src="../../vid/microlearning/microlearning-property-management.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>