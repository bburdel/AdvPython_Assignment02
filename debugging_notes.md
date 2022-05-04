# Logging as a Debugger
first run of loguru with the following parameters:
log = logger.add("out_{time}.log", backtrace=True, diagnose=True)
1. Making more than 1 file output...need to overwrite log?
2. KeyError in menu -- does not allow for user input of lower case menu choice or non-matching key 
    When I type in a capital menu choice, the program runs fine
    When I type in a lower case menu choice, KeyError exception raised. 
3. Lessons learned here -- you can wrap your code in a try/except to catch a specific exception and write that to file.

# Logging as Logging
This is so handy and really does alleviate the need for sprinkled throughout print statements. 
I have the logger.info messages printing out to a log and the console and I find them quite handy. As I tested out some
functions in a scratch environment, they were a great indicator of inappropriate iteration! If I could see an info message
print out to the console too many times it was a clue as to what I was doing. I certainly plan on using this in future
scripts.

# Debugger Observations (PySnooper)
    Using Assignment Read Me to catalog PySnooper/Loguru debugging experience.
	
1. Load the users database.
2. ~~Add a new user and confirm you get a success message.~~
	* Had no errors in my function call but colleague did and the error came from not returning a user object in their main.py add_user function.
3. ~~Try to add the same user ID again and confirm you get an error message.~~
	* Confirmed receipt of message -- "An error occurred while trying to add the new user." The ID was already in the database and therefore could not be added. Things funcitoning as they should.
4. Update the name of an existing user.
	* Trigged the TypeError exception due to not calling the user_collection (self) in the menu file. This then triggered an Attribute error 'UserCollection' object has no attribute update_user. Did you mean 'delete' ... I did not experience this issue as I had the correct function call. 
	Using loguru to write the log of the error to file, wrap the code in a try and except
5. Try to update the name of a non-existing user and confirm you get an error message.
6. Search for an existing user and return that user's email, name and last name.
	* Triggered AttributeError because there was no such attribute ".name"
	* Solution: changed line 78 to be result.user_id
7. Search for a non-existing user and return a message indicating that the user does not exist.
	* Nothing to debug, functions as expected. 
8. Delete an existing user.
	* worked as expected, nothing to debug
9. Try to delete a non-existing user and confirm you get an error message.
	* worked as expected, nothing to debug
10. Save the users database.
	* DO NOT HAVE FUNCTION RUNNING YET 4/30/22
11. Load the status database.
	* DO NOT HAVE FUNCTION RUNNING TO TEST
12. Add a new status and confirm you get a success message.
	* Confirmation new status message received
13. Try to add the same status ID again and confirm you get an error message.
	* Confirmed
14. Update the text of an existing status ID.
	* Unexpected function behavior. Received the output from the wrong if statement. 
	* Noticed the the wrong function called in PySnooper
	* Solution: Updated line 126 to have correct function call to main.update_status
	(was update status)
15. Try to update the text of a non-existing status ID and confirm you get an error message.
	* This functions as expected, got error message
16. Search for an existing status ID and return the ID of the user that created the status and the status text.
	* Issue 1: searching the wrong id -- user id instead of status id
	* Solution: line 144 in function changed to result.status_id
	* Issue 2: Paramaters were not in the correct order
	* Solution: PySnooper(depth=3) to walk through code and corrected parameter order/confirmed parameter in each file
17. Search for a non-existing status ID and return a message indicating that the status ID does not exist.
	* Functions as expected after fix for 16
18. Delete an existing status.
	* Functions as expected
19. Try to delete a non-existing status and confirm you get an error message.
	* Functions as expected
20. Save the status database.
21. ~~Make sure menu options are case-insensitive (i.e., typing "a" or "A" works in the same way).~~
	* On first run, a KeyError exception is triggered when typing in a lower case letter (correspinding to the menu choice.) Corrected with addition of .upper() to line 203 to resemble: menu_options[user_selection.upper()]()

Worked on assignment with Amanda Larson and Connor Lough.