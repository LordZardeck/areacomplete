## Using the plugin
The plugin has one function autocomplete which takes one argument with the following attributes:

	wordCount {Number} The amount of words you want to get from the position of the cursor in order to match it with your auto-complete list. usually this is set to 1.
	mode {String} could be "inner" or "outter" where inner is the inline mode where the auto-complete display the drop down list according to the cursot position. The outter mode works the same way as the twitter auto-complete works - at the bottom of the textarea. As for now i don't support the inner mode for IE - so the outter mode is set for IE. ( i can fix that but i don't have time.)
	on {Object}
		query {Function} will be called to query if there is any match for the user input. the function gets two params: text and callback. the text is the number of words you requested, and the callback should be called if you have anything to suggest to the text that was provided. You need to call the callback by providing an array of strings that you suggest. In case there is no match or no suggestion just call the callback with an empty array.
		selection {Function} This is not implemented yet, but i plan to support a callback of when the user has selected a suggestion from your list.
		
You can also style the list as you like by setting your own styles in the auto.css file.

## Styling the drop down menu
The plugin create a drop down menu to show the suggestion you have found for the current word that the user is typing. In order to style the to fits your needs, lets see the markup of the list:

	<ul class="auto-list" style="left: 91px; top: 113px; display: none;">
		<li data-value="daniel"><mark>d</mark>aniel</li>
		<li data-value="david"><mark>d</mark>avid</li>
	</ul>

So as you can see from this example, i set the drop down list with a "auto-list" class name, so you can style it however you want.
Here is the CSS i applied for the purpose of the demos:

	ul.auto-list{
		display: none;
		position: absolute;
		top: 0px;
		left: 0px;
		border: 1px solid green;
		background-color: #A3DF99;
		padding: 0;
		margin:0;
		list-style:none;
	}
	ul.auto-list > li:hover,
	ul.auto-list > li[data-selected=true]{
		background-color: #236574;
	}

	ul.auto-list > li{
		border: 1px solid gray;
		cursor: default;
		padding: 2px;

	}

	mark{
		font-weight: bold;
	}

That's it - it's that simple.