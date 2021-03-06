# Settlers of Definitely Not Katan Sequence Diagram Messages for Build at Location

## 1. Event\_Listener for mouse for Player\_Interaction activated to drag and drop an item to build.
### Player drags item to build to a location on the image representation of the board in the GUI.

## 2-5. GUI finds nearest location valid for item to build with the find() method.
### Calculations are done to find where the nearest pixel the item to build graphical asset was dropped corresponding to a valid location to build in the Game\_State Board attribute.

## 6-8. GUI interacts with Client\_Control class to send the appropriate information through the Send(location) method.
### Client\_Control and Host\_Control are the socket and message handling classes that manage interactions between the Client's GUI and the Host's Game\_Engine.

## 9. Host\_Control invokes the Game\_Engine class method to build\_at\_a\_location(location\_info)
### Game\_Engine's build\_at\_a\_location() method unpacks the parameter information from the Host\_Control and then grabs the relevant location from the Game\_State class when invoking the build\_an\_item(location\_info).

## 10. Game\_State class invokes the build\_an\_item() method which also invokes the player\_inventory() method.
### The player\_inventory() method takes the relevant information that was passed to the Game\_Engine class from the Host\_Control to check if the current\_player has the required resources and enough of the particular item to build left in its Inventory class.

## 11. Game\_State class player\_inventory() method requests the current\_player to invoke the check\_inventory() method.
### Part of checking whether or not the build\_an\_item() method can be properly invoked.

## 12. The current\_player attribute invokes the check\_inventory() method which invokes the Inventory check\_to\_build() method.
### The check\_to\_build() method checks whether or not the current\_player has the required Inventory attributes to build the item.

## 13. The Inventory class returns a boolean of whether or not the current\_player has the Inventory attributes to build the item.
### Returns TRUE to pass to current\_player if valid. Returns FALSE to pass to current\_player if not valid.

## 14. The current\_player returns the boolean result it was passed to the Game\_State player\_inventory() that is required to proceed with the build\_an\_item() method.
### Game\_State build\_an\_item() method returns a boolean from player\_inventory() invoked method.

## 15. The build\_an\_item() method is returned a boolean value from the player\_inventory() method.
### If the boolean is TRUE proceed with rest of build\_an\_item() method. 

## 16. Part one of checks for build\_an\_item() method is TRUE proceed to invoke next method in line also in Game\_State, check\_location()
### Method check\_location() invoked from Game\_State sending location information to the Board class inside of Game\_State.

## 17. Board class check\_location() method invoked from the invoking of check\_location() method inside of Game\_State class.
### Method check\_location() in Board class is passed the location information in parameters and is invoked.

## 18. Method check\_location() is called and checks the location for the item that is to be built.
### The method checks to see if the location is free to build on for the appropriate item being checked to build.
 
## 19. Method check\_location() returns a boolean value from the logic accessing the Location.
### Returns TRUE since location is a valid location to build the item on.

## 20. Method check\_location() inside of the Board class returns a boolean TRUE to the method check\_location() inside Game\_State.
### Second portion to checking whether or not the passed information from Client\_Control is accurate and a valid move for Current\_Player.

## 21. Boolean TRUE is returned back to the original call of build\_at\_a\_location() inside of the Game\_State class.
### This boolean value is the required value to proceed with the final portion of the build\_at\_a\_location() method.

## 22. The method build\_at\_a\_location() calls another helper method, build(), inside of Game\_State class.
### This method begins only if the previous helper methods in Game\_State called return TRUE boolean values. This ensures that no changes occur if the prerequisites are not fulfilled. 

## 23. The build() method in Game\_State accesses the Current\_Player object and invokes the build() method residing inside that as well. 
### This invocation of the Current\_Player's build() method is the method that accesses the Inventory class to deduct the resources and return a seed object.

## 24. The build() method in Current\_Player invokes the build() method inside of Inventory.
### The build() method inside of Inventory deducts the resources needed for the object to be built and returns a seed object.

## 25. Returning of seed object to the Current\_Player which will then link ownership to the seed object to the Current\_Player.
### Seed object was returned to Current\_Player which the ownership is set to the Current\_Player then.

## 26. Seed object is returned to the build() method inside of Game\_State.
### Seed object is returned to finish being manipulated inside of build() method, filling out and finishing populating the relevant information for the object.

## 27. The build() method takes the returned seed object and accesses the Board class to link the location to the seed object.
### With the previous information given at the initial passing between Client and Host, access the board and link location to that seed object.

## 28. Once finished linking the location to the object, link the object to the location and return TRUE boolean value.
### TRUE boolean value is passed back through the build() method in Game\_State. 

## 29. TRUE boolean value returned after finishing of build() method to build\_an\_item() method in order to proceed.
### This boolean value is just a confirmation of whether or not build\_an\_item() method was able to be fully complete for the information given.

## 30. Game\_State class finishes the call of build\_an\_item() method which also returns a boolean value of TRUE to the Game\_Engine class finishing the Game\_State access in the built\_at\_a\_location() method in Game\_Engine.
### This boolean value allows the Game\_Engine to determine what is next logically.

## 31. Game\_Engine is returned a TRUE boolean value for build\_at\_a\_location() method invocation, this tells the Game\_Engine to then send the Game\_State to the Host\_Control.
### Host\_Control receives the newly updated Game\_State.

## 32-34. Host\_Control finishes the initial logic to invoke the Game\_Engine and returns the Game\_State it received to the Client\_Control over socket which then sends the same Game\_State over to the GUI class calling invoking the update\_game\_state() method.

## 35. The update\_game\_state(new\_game\_state) method accesses the Game\_State that is representative of the previous Game\_State before the Current\_Player attempted any interaction and sets it to the new\_game\_state parameter.
### Game\_State is now equal to new\_game\_state.

## 36. The update\_game\_state() method should return true and GUI then invokes the update\_GUI() method which updates the graphical representation of the current Game\_State.
### Method update\_GUI() invoked after receiving the TRUE boolean value.

## 37. Method update\_GUI() properly updates the graphical representation of the current Game\_State for the current\_player to interact with.
### Graphical representation of current Game\_State is updated and the current\_player is allowed to take further actions on the GUI.