# promiseErrorHandler

## Use
Your component can extend this

`
<aura:component ... extends="promiseErrorHandler">
`

## Call Apex

`
//assuming your component is named component and your helper is named helper

var action=component.get("c.myApexMethod");
action.setParams("param1" : "value1");
helper.executeAction(component, action) //if helper, use this instead of helper
.then($A.getCallback(function result){

}).then



`


