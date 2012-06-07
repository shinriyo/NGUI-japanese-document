===============
12.Chat Window
===============

This example shows how to create a simple chat window. A chat window is made up of two main components:

The Input field where a user can type something.

An area with text.

Input field is easy, and is covered in the 7th Tutorial, but the text area? Equally simple, actually: UITextList. This script allows you to dynamically create text lines and arrange them in either the Text Style (scroll position of 0 being the top), or the Chat Style (scroll position of 0 being on the bottom).

Now, I should probably mention that this script does not actually create any labels. It simply works with an existing label you specify and fills its contents using its own list of text entries and the current scroll value. You can also specify the size of the text area as well as the maximum number of paragraphs before they start getting recycled (with the oldest one being reused to create the latest).

The scrolling is accomplished by another feature built into UITextList, but can be turned off via a checkbox on the script.

Last but not least, the actual input activation is handled via ChatInput — a custom script written for this example. It’s pretty short, only 70 lines — and all it does inside is:

Populates the Text List with some dummy data on Start().

Selects the input if the Enter key gets pressed.

Calls UITextList.Add with the input field’s text when OnSubmit() message is received (sent by the Input Field), then clears the input field’s text.

End result? Fully functional (albeit a little ugly) chat window that will work on all devices.

