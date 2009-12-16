Interfaces
===========

Interfaces provides some Interface Logic to MooTools-Classes. It also provides a simple Interface Object

How to use
----------

First, you need to define your Interface by using the Interface Class. It takes two arguments - the first one is the (necessary) Name of the Interface as a string, the second one is an Object which will define the Interface.

In the Interface Definition, you can declare empty functions/properties, which shall be implemented by the class which will make use of the interface. You can also define some interfaces to be needed by using an Property "Interfaces" (Value(s) have to be valid Interface Objects ).

Now, you can make use of the Interface in Classes, by using the Property "Interfaces". It will check, if you the Interface is implemented and throw an error, if not.

Have fun! :-)

	#JS
	INotifyPropertyChanged = new Interface( "INotifyPropertyChanged", {
		Interfaces: [ITypeIdentifyable], /* This wouldnt be needed for an INotifyPropertyChanged Interface */
		MyProperty: String,
		NotifyPropertyChanged: function() {},
		Set: function() {}
	});
	
	ITypeIdentifyable = new Interface( "ITypeIdentifyable", {
		Type: String
	});
	
	var NotifyPropertyChanged = new Class({
		Implements: Events,
		Interfaces: [ INotifyPropertyChanged, ITypeIdentifyable ],
		
		/* ITypeIdentifyable Interface implementation */
		Type: "NotifyPropertyChanged",
		
		/* INotifyPropertyChanged Interface implementation */
		MyProperty: 0,
		NotifyPropertyChanged: function() {
			/* Some logic */
		},
		Set: function( val ) {
			/* Some logic */
		}
	});
