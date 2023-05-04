Download Link: https://assignmentchef.com/product/solved-cs6952-homework-5
<br>
<h1>1.      Matrix: 40 Points</h1>

<strong>File: </strong>matrix.cpp

In this problem you will implement arbitrary sized matrix that can hold elements of any type (defined by a template parameter T). You will create a class <sub>Matrix </sub>which has two constructors <sub>Matrix() </sub>(creates empty matrix) and <sub>Matrix(int m, </sub>int n) (creates m by n matrix). The destructor <sub>~Matrix() </sub>needs to deallocate the memory which holds matrix elements. Apply <strong><sub>rule of three</sub></strong>, so add copy constructor and assignment operator. Additionally, you need to implement following operators:

<ul>

 <li><sub>operator* </sub>(multiplies two matrices and returns new matrix),</li>

 <li><sub>operator+ </sub>(adds two matrices and returns new matrix),</li>

 <li><sub>operator[] </sub>(returns an element addressed with one index),</li>

 <li><sub>operator() </sub>(returns an element addressed with two indices),</li>

 <li><sub>operator&lt;&lt; </sub>(sends a matrix to ostream; do not use std::cout in the operator), and</li>

 <li><sub>operator&gt;&gt; </sub>(reads a matrix).</li>

</ul>

The matrix element types tested in the main will only be <sub>double </sub>and <sub>int </sub>thus you need two instances of the templated Matrix. As usual, the input will contain the number of cases and for each case the operation to perform, the type of the operands, and the two matrices. The size of each matrix is specified by two numbers (m – number of rows and n – number of columns) and its elements. After performing the specified operation you need to print the resulting matrix. All inputs will be valid, so there is no need to check if the input are numbers or that the matrix sizes are compatible.

<h2>Example Input</h2>

3 multiply int

2 3

1 2 3

5 6 7

3 5

-9 8 7 6 5

4 3 2 1 0

<ul>

 <li>0 0 1 3</li>

</ul>

add double

<ul>

 <li>2</li>

</ul>

1 0

0 1

2 2

5 2

3 4

add int

1 3

10 9 -98

1 3

10 0 99

<h2>Example Output</h2>

Case 0:

2 14 11 11 14 -14 58 47 43 46 Case 1:

6 2

3 5

Case 2: 20 9 1

<h1>2.      Contact Manager: 60 Points</h1>

<strong>Files:</strong>

<ul>

 <li>cpp, contact.h</li>

 <li>cpp</li>

</ul>

What makes associative containers like <sub>std::map </sub>powerful and useful is that they can associate keys with values and quickly find the value associated with a specific key. For example in a contact manager we want to be able to associate a person’s name with some information about them (like phone number, e–mail, etc.) and quickly look up this information given a first and last name. In this problem you will create a contact management tool that will store some information about the user’s contacts and allow them to list them, add or remove contacts and search for a contact by name.

<h2>Contact Information</h2>

For each contact you will store the following data:

<ul>

 <li>First name</li>

 <li>Last name</li>

 <li>Phone number. Note: while phone numbers are “numbers” they are not numeric (like an int), they are strings of characters in [0, 9]. <strong><sub>Do not </sub></strong>store the phone number as an int. • E–mail address</li>

</ul>

The contact information should be stored in a class (maybe called <sub>Contact</sub>) declared in <sub>contact.h </sub>and defined in <sub>contact.cpp</sub>. Your contact class should also provide a default constructor (one that takes no parameters) as this is needed by the <sub>std::map </sub>to perform some operations.

<h2>User Interaction</h2>

The user will need to be able to interact with the contact manager by adding/removing contacts, searching by name and listing all contacts in the manager. They should also be able to exit the manager. To indicate to the user that the program is awaiting their input you should print a caret (<sub>&gt;</sub>) followed by a space as a prompt. In the examples below the user input and expected output are shown interleaved, with the user input preceeded by the prompt.

After receiving and executing the user’s command you should return to the initial input prompt so they can enter another command. Examples of a full interactive session are shown after the details of each command. To help you start this is what your main function should look like to loop over and handle a user’s commands until they enter “exit”. You can use this as starter code for your program. Note that there is no cases loop in this assignment, just the user interaction loop.

int main(){ std::string cmd; <strong>do </strong>{ <strong>if </strong>(cmd == “exit”){ <strong>break</strong>;

} <strong>else if </strong>(cmd == “list”){

<em>// List contacts in the manager</em>

} <strong>else if </strong>(cmd == “add”){ <em>// Add a contact to the manager </em>} <strong>else if </strong>(cmd == “remove”){

<em>// Remove a contact from the manager</em>

} <strong>else if </strong>(cmd == “find”){

<em>// Find a contact in the manager</em>

}

<em>// Print a terminal prompt so the user knows // we’re waiting for their input</em>

std::cout &lt;&lt; “&gt; “; } <strong>while </strong>(std::cin &gt;&gt; cmd); <strong>return </strong>0;

}

<h3>Listing All Contacts</h3>

When the user enters the <sub>list </sub>command and you should print out the first and last names of all the contacts in the manager. If there are no contacts in the manager you should just print <sub>no contacts</sub>. The contacts should be printed in alphabetical order, sorted by last name then by first name. This sorting will be done automatically for you if you build the key in the <sub>std::map </sub>properly.

Example: The manager contains three people: Grace Hopper, Dennis Ritchie and Leslie Lamport

&gt; list

Hopper, Grace

Lamport, Leslie

Ritchie, Dennis

Example: The manager is empty.

&gt; list no contacts

<h3>Adding a Contact</h3>

When the user enters the <sub>add </sub>command you should prompt them to enter the first name, last name, phone number and e–mail address for the contact, one after the other. You should print a prompt each time so the user knows what the program is expecting them to input. First you should read the first name and print the prompt <sub>first name:</sub>, for the last name the prompt is <sub>last name:</sub>, for the phone number it’s <sub>phone number: </sub>and for the e–mail address it’s <sub>e-mail:</sub>. <strong>If a contact with same first and last name is already in contact manager, then overwrite it with this new contact.</strong>

<strong>Note </strong>that there is a trailing space after the colon printed for each prompt so the user’s input doesn’t run right against the prompt.

Example: The user wants to add Ada Lovelace as a contact.

&gt; add first name: Ada last name: Lovelace phone number: 555123456 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="3e5f5a5f7e5251485b525f5d5b10535f4a56535f5752">[email protected]</a>

<h3>Removing a Contact</h3>

When the user enters the <sub>remove </sub>command you should prompt them to enter the first and last name of the contact, with the same prompts used when adding a contact (<sub>first name: </sub>and <sub>last name:</sub>). If the contact is found they should be removed from the list and you should print a confirmation of the form <sub>removed </sub>FIRST LAST where FIRST and LAST are the first and last name of the contact that was removed. If no contact is found with the name entered you should print out contact not found.

Example: The user wants to remove Richard Stallman, who is in the manager. &gt; remove first name: Richard last name: Stallman removed Richard Stallman

Example: The user wants to remove John McCarthy, who is not in the manager.

&gt; remove first name: John last name: McCarthy contact not found

<h3>Finding a Contact</h3>

When the user enters the <sub>find </sub>command you should prompt them to enter the first and last name to search for, using the same prompt style as before. If the contact is found you should print out the full information about the contact (the name, phone number and e–mail address). If the contact is not found you should print out contact not found.

If a contact is found the contact’s information should be printed out as:

Name: FIRST LAST

Phone Number: PHONENUMBER E-mail: EMAIL

Where FIRST, LAST, PHONENUMBER and EMAIL correspond to the contact’s data.

Example: The user searches for Donald Knuth, who is in the manager.

&gt; find first name: Donald last name: Knuth Name: Donald Knuth

Phone Number: 555898123

E-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="402b2e35342800242f2e212c246e3425382d21292c">[email protected]</a>

Example: The user searches for Edsger Dijkstra, who is not in the manager.

&gt; find first name: Edsger last name: Dijkstra contact not found

<h3>Exiting the Manager</h3>

When the user enters the <sub>exit </sub>command your program should exit as done in the main function provided for you above. There is no example use case as the only thing your program should do after receiving the “exit” command is exit.

<h2>Some Notes and Hints on std::map</h2>

You should use a <sub><a href="http://en.cppreference.com/w/cpp/container/map">std::map</a> </sub>to store the contact information where the keys will be some combination of their first and last name (as people can have the same first or last name, but not both) and the value will be your <sub>Contact </sub>struct. The actual values returned by the iterator over your map will be a <sub>std::pair&lt;Key, </sub>Value&gt; where key would likely be <sub>std::string </sub>and Value would be a <sub>Contact</sub>. To access each element of the pair you can use <sub>first </sub>or <sub>second </sub>as shown below.

std::map&lt;std::string, int&gt; my_map{{“hello”, 4}, {“bob”, 2}}; <strong>for </strong>(const <strong>auto </strong>&amp;e : my_map){

<em>// first accesses the key, second accesses the value</em>

std::cout &lt;&lt; e.first &lt;&lt; ” mapped to ” &lt;&lt; e.second &lt;&lt; “
”; }

This code will print:

bob mapped to 2 hello mapped to 4

To insert into a map we can index it by the key with <sub><a href="http://en.cppreference.com/w/cpp/container/map/operator_at">operator[]</a></sub><a href="http://en.cppreference.com/w/cpp/container/map/operator_at">.</a> If the key is not found a new entry is created using the default constructor and a reference returned (this is why we need a default constructor for Contact), if the key is found the existing entry will be returned. std::map&lt;std::string, int&gt; my_map{{“hello”, 4}, {“bob”, 2}}; <em>// Create key, value pair for joe and set it to 10</em>

std::string joe = “joe”; my_map[joe] = 10;

<em>// Update the existing entry for hello</em>

my_map[“hello”] = 5; <strong>for </strong>(const <strong>auto </strong>&amp;e : my_map){

<em>// first accesses the key, second accesses the value</em>

std::cout &lt;&lt; e.first &lt;&lt; ” mapped to ” &lt;&lt; e.second &lt;&lt; “
”; }

This code will print:

bob mapped to 2 hello mapped to 5 joe mapped to 10

To find an entry by its key you can use <sub><a href="http://en.cppreference.com/w/cpp/container/map/find">find</a></sub><a href="http://en.cppreference.com/w/cpp/container/map/find">,</a> see the interactive example on the documentation page for usage, and for how to see if the key was not found. Since the map will create the entry if it’s not found when indexing with <sub>operator[] </sub>you must use <sub>find </sub>to see if a key exists in the map. <sub>find </sub>returns an iterator so we can use <sub>find </sub>and <sub><a href="http://en.cppreference.com/w/cpp/container/map/erase">erase</a> </sub>to remove an element by its key since <sub>erase </sub>takes the iterator to the element that we want to remove.

You can assume that you will receive valid input and commands and for simplicity that case does matter, for example Dennis Ritchie is a different person than dennis ritchie.

<h2>Example Usage</h2>

<h3>Interactive Session</h3>

Since the program is interactive just reading the output can be kind of confusing. Instead you can copy-paste the sample input (from <sub>contacts_stdin.txt</sub>) to the console to see what the actual usage would look like. You should see the following if you paste the sample input into your console. There is no case loop for this problem, just the user interaction loop.

&gt; list no contacts &gt; add first name: Ada last name: Lovelace phone number: 555123456 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="aecfcacfeec2c1d8cbc2cfcdcb80c3cfdac6c3cfc7c2">[email protected]</a>

&gt; list

Lovelace, Ada &gt; add first name: Grace last name: Hopper phone number: 555823457 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="59313629293c2b193d3c3b2c3e3e30373e">[email protected]</a>

&gt; add first name: Dennis last name: Ritchie phone number: 555898123 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="187c7d7676716b587d75797174">[email protected]</a> &gt; add first name: Leslie last name: Lamport phone number: 000912931 e-mail: leslie.lamport

&gt; list

Hopper, Grace

Lamport, Leslie Lovelace, Ada

Ritchie, Dennis

&gt; remove first name: Dennis last name: Ritchie removed Dennis Ritchie &gt; remove first name: Dennis last name: Ritchie contact not found &gt; list

Hopper, Grace

Lamport, Leslie

Lovelace, Ada &gt; find first name: Dennis last name: Ritchie contact not found &gt; find first name: Leslie last name: Lamport Name: Leslie Lamport

Phone Number: 000912931

E-mail: leslie.lamport &gt; add first name: Dennis last name: Ritchie phone number: 555898123 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="4125242f2f283201242c20282d73">[email protected]</a> &gt; list

Hopper, Grace

Lamport, Leslie

Lovelace, Ada

Ritchie, Dennis &gt; find first name: Dennis last name: Ritchie Name: Dennis Ritchie

Phone Number: 555898123

E-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="92f6f7fcfcfbe1d2f7fff3fbfea0">[email protected]</a> &gt; add first name: Dennis last name: Ritchie phone number: 555898123 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="4b2f2e252522380b2e262a2227">[email protected]</a> &gt; add first name: Bob last name: Ritchie phone number: 555898123 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="d9bdbcb7b7b0aa99bcb4b8b0b5">[email protected]</a> &gt; add first name: Bob last name: Jackson phone number: 555898123 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="a1c5c4cfcfc8d2e1c4ccc0c8cd">[email protected]</a> &gt; add first name: Jack last name: Jackson phone number: 555898123 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="80e4e5eeeee9f3c0e5ede1e9ec">[email protected]</a> &gt; add first name: Jack last name: Jackson phone number: 555898123 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="6b0f0e050502182b0e060a0207">[email protected]</a> &gt; add first name: Grace last name: Hopper phone number: 5551020001238123 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="baddc8dbd9dffadfd7dbd3d6">[email protected]</a> &gt; add first name: Brian last name: Kernighan phone number: 555 e-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="a8cadac1c9c686c3cddac6c1cfc0c9c6e8cdc5c9c1c4">[email protected]</a>

&gt; list

Hopper, Grace Jackson, Bob

Jackson, Jack

Kernighan, Brian

Lamport, Leslie

Lovelace, Ada

Ritchie, Bob

Ritchie, Dennis &gt; exit

<h3>Input/Output Redirected Session</h3>

See the <sub>stdin_stdout.zip </sub>file for the input/output files for this example since it’s a bit hard to read the output here due to long lines. Input: list

add Ada

Lovelace 555123456 <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="72131613321e1d04171e1311175c1f13061a1f131b1e">[email protected]</a> list add Grace Hopper 555823457 <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="92fafde2e2f7e0d2f6f7f0e7f5f5fbfcf5">[email protected]</a> add Dennis Ritchie 555898123 <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="1f7b7a7171766c5f7a727e7673">[email protected]</a> add Leslie Lamport 000912931 leslie.lamport list remove Dennis Ritchie remove Dennis Ritchie list find Dennis Ritchie find Leslie Lamport add Dennis Ritchie 555898123 <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="d6b2b3b8b8bfa596b3bbb7bfbae4">[email protected]</a> list find Dennis Ritchie add Dennis

Ritchie 555898123 <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="66020308080f1526030b070f0a">[email protected]</a> add Bob

Ritchie 555898123 <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="5b3f3e353532281b3e363a3237">[email protected]</a> add Bob

Jackson 555898123 <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="fc98999292958fbc99919d9590">[email protected]</a> add Jack

Jackson 555898123 <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="94f0f1fafafde7d4f1f9f5fdf8">[email protected]</a> add Jack

Jackson 555898123 <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="9afefff4f4f3e9dafff7fbf3f6">[email protected]</a> add Grace

Hopper 5551020001238123 <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="f29580939197b2979f939b9e">[email protected]</a> add Brian

Kernighan 555 <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="7e1c0c171f1050151b0c101719161f103e1b131f1712">[email protected]</a> list exit

Expected Output

&gt; no contacts

&gt; first name: last name: phone number: e-mail: &gt; Lovelace, Ada

&gt; first name: last name: phone number: e-mail: &gt; first name: last name: phone number: e-mail

Lamport, Leslie Lovelace, Ada

Ritchie, Dennis

&gt; first name: last name: removed Dennis Ritchie

&gt; first name: last name: contact not found

&gt; Hopper, Grace

Lamport, Leslie

Lovelace, Ada

&gt; first name: last name: contact not found

&gt; first name: last name: Name: Leslie Lamport

Phone Number: 000912931

E-mail: leslie.lamport

&gt; first name: last name: phone number: e-mail: &gt; Hopper, Grace

Lamport, Leslie Lovelace, Ada

Ritchie, Dennis

&gt; first name: last name: Name: Dennis Ritchie

Phone Number: 555898123

E-mail: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="d3b7b6bdbdbaa093b6beb2babfe1">[email protected]</a>

&gt; first name: last name: phone number: e-mail: &gt; first name: last name: phone number: e-mail

Jackson, Bob

Jackson, Jack

Kernighan, Brian

Lamport, Leslie

Lovelace, Ada

Ritchie, Bob

Ritchie, Dennis

&gt;