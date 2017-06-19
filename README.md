# promiseErrorHandler

## Use
Your component can extend this

`
<aura:component ... extends="promiseErrorHandler">
`

## Call Apex

```
//assuming your component is named component and your helper is named helper
var action=component.get("c.myApexMethod");
helper.executeAction(component, action) //if helper, use this instead of helper
	.then($A.getCallback(function (result){
		//do something with the result
	}));
```

### Setting Params and other stuff

you can add `action.setParams({"myParam" : "paramValue"})` and/or `action.setStorable` (not recommended) before passing it to the executeAction.

## Chaining Promises
```
//assuming your component is named component and your helper is named helper
var action=component.get("c.myApexMethod");
helper.executeAction(component, action) //if helper, use this instead of helper
	.then($A.getCallback(function (result){
		//do another apex call by returning a promise
		return helper.executeAction(component, action);
	})).then($A.getCallback(function (result){
		//do something with that 2nd result
	}))
```

## Errors
The LightningErrorHandler is going to handle the basic errors (toasting them).  If you need to do something more (example: set or reset local state variables or attributes) you can do that with the normal promises error function, the 2nd thing that gets passed in

```
helper.executeAction(component, action) //if helper, use this instead of helper
	.then($A.getCallback(function (result){
		//do something with the result
	}), $A.getCallback (function (error){
		//do something about that error
	}));
```

Errors in a chain only need that error thing on the last one in the chain.




