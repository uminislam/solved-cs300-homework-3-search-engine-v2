Download Link: https://assignmentchef.com/product/solved-cs300-homework-3-search-engine-v2
<br>
<h2>Brief Description</h2>

In this homework, you will write a search engine as in the 2<sup>nd</sup>​ Homework. Additionally, you will compare the speed of two different data structures for your search engine architecture. The search engines in real life search hundreds of millions web pages to see if they have the words that you have typed, and they can do this for thousands of users at a given time. In order to do these searches really fast, search engines such as Google do a lot of what we call preprocessing of the pages they search; that is, they transform the contents of a web page (which for the purposes of this homework, we will assume it consists of only strings) into a structure that can be searched very fast.

In this homework, you are going to preprocess the documents provided to you. For each unique word, you will insert a node into both of your data structures, i.e. Binary Search Tree (BST) and Hash Table. Of course, you will also keep track of the details such as the document name which the word appears in and the number of times the word appears in each document. So, you need to implement a templated BST and Hash Table.

Using both of the data structures, you need to show the number of times that every queried word appears in. After that, you will compare the speed of them. You may use and modify the data structures and classes you implemented in Homework2.

<strong> </strong>

<h3>BST (​ Binary Search Tree)</h3>

You may modify the AVL Tree class that you have implemented in Homework2 by removing the balancing (rotation) parts of it.

<strong> </strong>

<h2>HashTable</h2>

You are going to implement a hash table data structure adopting any of the collision handling strategies, such as separate chaining, linear or quadratic probing, etc. You may use any strategy which may accelerate the HashTable operations.

You need to rehash every time when the load of the table exceeds the load factor that you have determined for your HashTable. For each rehash operation you need to print the internal information of the HashTable such as the previous capacity, current capacity, previous load, and the current load. The load will be calculated as (item count / capacity).

Additionally, you need to develop a hash function aiming to have collision free hash values for different WordItem structs.

<h2>Program Flow</h2>

You need to get the number of the documents that you need to preprocess first. Then, after getting the names of all documents from the console, you need to preprocess all the text in the documents. Only the alphabetical characters are considered, and the unique words need to be case insensitive (for example; “izmir” and “Izmir” are the same). <strong>The</strong>​<strong> rest (such as digits or punctuation characters) are processed as the separator for the words.</strong> For each unique word appearing in the text, you need to insert a new node into the tree and the hashtable.

If the node is already there, you need to update the node with the information about this document. For example; you have preprocessed the “a.txt” document first and there is only one “the” word in this document. You need to insert “the” word into the data structures. Then, while preprocessing the “b.txt” document, “the” word appears 4 times. So, you need to add this information ({“b.txt”, 4}) into the existing item in your data structures and the item of “the” word becomes {{“a.txt”, 1}, {“b.txt”, 4}}.

After you preprocess all the documents, you need to get a query from the console which consists of a line of strings (HINT: You may use getline(cin,​ line)).​ This line might consist of more than one word. Then, <strong>you</strong>​<strong> need to output the document names which all words in the query appear including the number of times that each word appears in that document. </strong>

For the comparison of the speed of using different data structures, you need to perform the same operation, processing the query and building the result, without printing the result 20 times and taking the average timing.




<strong>Hint</strong> <strong>struct</strong> ​ <strong>DocumentItem</strong>​        <strong> {</strong>​        <strong>string documentName;</strong> <strong>int count;</strong>

<strong>};</strong>




<strong>struct</strong> ​ <strong>WordItem</strong>​  <strong> {</strong>​        <strong>string word;</strong>

<strong><em>// List of DocumentItem’s. </em></strong>

};










<strong> </strong>

<strong> </strong>

<h2>For timing</h2>

<strong>int</strong>​<strong> k = 20; </strong>

<strong>auto</strong>​<strong> start = std::chrono::</strong><strong>high_resolution_clock</strong>​   <strong>::</strong>​ <strong>now(); </strong><strong>for</strong>​<strong> (</strong>​<strong>int</strong>​<strong> i = 0; i &lt; k; i++) </strong>

<strong>{ </strong>

<strong><em>// QueryDocuments(with BST); </em></strong>

<strong>} </strong>

<strong>auto</strong>​<strong> BSTTime = std::chrono::duration_cast&lt;std::chrono::</strong>​<strong>nanoseconds</strong>​<strong>&gt;  </strong>

<strong>(std::chrono::</strong>​<strong>high_resolution_clock</strong>​<strong>::now() </strong>​<strong>–</strong><strong> start); </strong>

<strong>cout </strong>​<strong>&lt;&lt;</strong>​ ​<strong>“
Time: “</strong>​ ​<strong>&lt;&lt;</strong>​<strong> BSTTime.count() / k </strong>​<strong>&lt;&lt;</strong>​ ​<strong>“
”</strong>​<strong>; start </strong><strong>=</strong>​<strong> std::chrono::</strong>​             <strong>high_resolution_clock</strong>​        <strong>::</strong>​ <strong>now(); </strong><strong>for</strong>​<strong> (</strong>​<strong>int</strong>​<strong> i = 0; i &lt; k; i++) </strong>

<strong>{ </strong>

<strong><em>// QueryDocuments (with hashtable); </em></strong>

<strong>} </strong>

<strong>auto</strong>​<strong> HTTime = std::chrono::duration_cast&lt;std::chrono::</strong>​<strong>nanoseconds</strong>​<strong>&gt;  </strong>

<strong>(std::chrono::</strong><strong>high_resolution_clock</strong>​ <strong>::</strong>​ <strong>now() </strong><strong>–</strong>​<strong> start);</strong>​

<strong>cout </strong>​<strong>&lt;&lt;</strong>​ ​<strong>“
Time: “</strong>​ ​<strong>&lt;&lt;</strong>​<strong> HTTime.count() / k </strong>​<strong>&lt;&lt;</strong>​ ​<strong>“
”</strong>​<strong>; </strong>

<strong> </strong>

<strong> </strong>

<h2>Rules</h2>

<ul>

 <li>HashTable implementation <u>​<strong>must be faster</strong></u>​ than the BST implementation. Otherwise your grade will be 0.</li>

 <li>Every non-alphabetical character is considered as a separator (​<strong><u>different than HW2</u></strong>​). This rule applies for both the text in input files and queried words.</li>

</ul>

For example; “face2face” = “face.face” = “face:facE” = “face face”

<ul>

 <li>The resulting HashTable load factor (λ) <strong><u>must</u></strong>​<strong><u> be larger than 0.25</u></strong> and <strong><u>lower</u></strong><u>​<strong> than 0.9</strong></u> (0.25 &lt; λ &lt; 0.9) whatever the input size is. Otherwise your grade will be 0. Pick the upper bound of load value that gives you best results in terms of speed.</li>

</ul>

<strong> </strong>

<h2>Input</h2>

First, input is the number of documents that is going to be preprocessed. Then the file names will be received from the console. Then the queried words will be taken from the user as one line of words.

<h3>Output</h3>

While preprocessing the files, you need to print the information about the HashTable every time when the rehashing occurs, i.e. display the previous capacity, the previous load, current capacity, current load, and the number of items in the HashTable. After all preprocessing is finished, you need to print the final item count in the HashTable and the current load factor λ.

After the user enters the query words, you need to print the document names and the number of times each queried word appears in that document.

Lastly you compute the time it takes to do the query with each data structure you’ve implemented (BST, Hash Table) and display them with the speedup ratio of these timing values compared to each other. In addition you display the ranking of the times of each sort algorithm.

<strong> </strong>

<h2>Sample Run 1</h2>

Enter number of input files: 1 Enter 1. file name: a.txt rehashed…

previous table size:53, new table size: 107, current unique word count 49, current load factor: 0.448598 rehashed…

previous table size:107, new table size: 223, current unique word count 98, current load factor: 0.434978 rehashed…

previous table size:223, new table size: 449, current unique word count 202, current load factor: 0.447661 rehashed…

previous table size:449, new table size: 907, current unique word count 406, current load factor: 0.446527 rehashed…

previous table size:907, new table size: 1823, current unique word count 818, current load factor: 0.448162 rehashed…

previous table size:1823, new table size: 3659, current unique word count

1642, current load factor: 0.448483 rehashed…

previous table size:3659, new table size: 7321, current unique word count

3295, current load factor: 0.449939 rehashed…

previous table size:7321, new table size: 14653, current unique word count

6590, current load factor: 0.449669







After preprocessing, the unique word count is 8475. Current load ratio is

0.57838 Enter queried words in one line: above in Document a.txt, above found 12 times. in Document a.txt, above found 12 times.




Time: 9896

Time: 1797

Speed Up: 5.50544




<strong> </strong>

Enter number of input files: 2

Enter 1. file name: a.txt Enter 2. file name: b.txt rehashed…

previous table size:53, new table size: 107, current unique word count 49, current load factor: 0.448598 rehashed…

previous table size:107, new table size: 223, current unique word count 98, current load factor: 0.434978 rehashed…

previous table size:223, new table size: 449, current unique word count 202, current load factor: 0.447661 rehashed…

previous table size:449, new table size: 907, current unique word count 406, current load factor: 0.446527 rehashed…

previous table size:907, new table size: 1823, current unique word count 818, current load factor: 0.448162 rehashed…

previous table size:1823, new table size: 3659, current unique word count

1642, current load factor: 0.448483 rehashed…

previous table size:3659, new table size: 7321, current unique word count

3295, current load factor: 0.449939 rehashed…

previous table size:7321, new table size: 14653, current unique word count

6590, current load factor: 0.449669 rehashed…

previous table size:14653, new table size: 29311, current unique word count

13189, current load factor: 0.449933







After preprocessing, the unique word count is 15965. Current load ratio is

0.544676

Enter queried words in one line: above:aberration

in Document a.txt, above found 12 times, aberration found 1 times. in Document a.txt, above found 12 times, aberration found 1 times.




Time: 14933




Time: 3081

Speed Up: 4.84613



















<strong> </strong>

Enter number of input files: 3

Enter 1. file name: a.txt

Enter 2. file name: b.txt Enter 3. file name: c.txt rehashed…

previous table size:53, new table size: 107, current unique word count 49, current load factor: 0.448598 rehashed…

previous table size:107, new table size: 223, current unique word count 98, current load factor: 0.434978 rehashed…

previous table size:223, new table size: 449, current unique word count 202, current load factor: 0.447661 rehashed…

previous table size:449, new table size: 907, current unique word count 406, current load factor: 0.446527 rehashed…

previous table size:907, new table size: 1823, current unique word count 818, current load factor: 0.448162 rehashed…

previous table size:1823, new table size: 3659, current unique word count

1642, current load factor: 0.448483 rehashed…

previous table size:3659, new table size: 7321, current unique word count

3295, current load factor: 0.449939 rehashed…

previous table size:7321, new table size: 14653, current unique word count

6590, current load factor: 0.449669 rehashed…

previous table size:14653, new table size: 29311, current unique word count

13189, current load factor: 0.449933







After preprocessing, the unique word count is 22320. Current load ratio is

0.761489

Enter queried words in one line: a the-has been

No document contains the given query

No document contains the given query




Time: 5669

Time: 5076

Speed Up: 1.11673

























Enter number of input files: 2

Enter 1. file name: a.txt Enter 2. file name: d.txt rehashed…

previous table size:53, new table size: 107, current unique word count 49, current load factor: 0.448598 rehashed…

previous table size:107, new table size: 223, current unique word count 98, current load factor: 0.434978 rehashed…

previous table size:223, new table size: 449, current unique word count 202, current load factor: 0.447661 rehashed…

previous table size:449, new table size: 907, current unique word count 406, current load factor: 0.446527 rehashed…

previous table size:907, new table size: 1823, current unique word count 818, current load factor: 0.448162 rehashed…

previous table size:1823, new table size: 3659, current unique word count

1642, current load factor: 0.448483 rehashed…

previous table size:3659, new table size: 7321, current unique word count

3295, current load factor: 0.449939 rehashed…

previous table size:7321, new table size: 14653, current unique word count

6590, current load factor: 0.449669







After preprocessing, the unique word count is 8575. Current load ratio is

0.585204

Enter queried words in one line: A: in Document a.txt, a found 87 times. in Document d.txt, a found 4 times. in Document a.txt, a found 87 times. in Document d.txt, a found 4 times.




Time: 2390

Time: 1975

Speed Up: 1.21002

























<h1>General Rules and Guidelines about Homeworks</h1>




The following rules and guidelines will be applicable to all homeworks, unless otherwise noted.




<strong>How to get help?</strong>

You may ask questions to TAs (Teaching Assistants) of CS300. Office hours of TAs are at the syllabus. Recitations will partially be dedicated to clarify the issues related to homework, so it is to your benefit to attend recitations.




<h2>What and Where to Submit</h2>

Please see the detailed instructions below/in the next page. The submission steps will get natural/easy for later homeworks.




<h2>Grading and Objections</h2>

<u>Careful about the semi-automatic grading:</u> Your programs will be graded using a semi-automated system. Therefore, you should follow the guidelines about input and output order; moreover, you should also use same prompts as given in the Sample Runs. Otherwise semi-automated grading process will fail for your homework, and you may get a zero, or in the best scenario you will lose points.




<u>Grading:</u>

<ul>

 <li>Late penalty is 10% off the full grade and only one late day is allowed.</li>

 <li><strong>Having a correct program is necessary, but not sufficient to get the full grade. Comments, indentation, meaningful and understandable identifier names, informative introduction and prompts, and especially proper use of required functions, unnecessarily long programs (which is bad) and unnecessary code duplications will also affect your grade.</strong></li>

 <li>Please submit your own work only (even if it is not working). It is really easy to find “simil​ ar​ ”​ programs!</li>

 <li>For detailed rules and course policy on plagiarism, please check out</li>

</ul>







<a href="http://myweb.sabanciuniv.edu/gulsend/courses/cs201/plagiarism/">http://myweb.sabanciuniv.edu/gulsend/courses/cs201/plagiarism/</a>







<u>Grade announcements:</u> Grades will be posted in SUCourse, and you will get an Announcement at the same time. You will find the grading policy and test cases in that announcement.




<u>Grade objections:</u> It is your right to object to your grade if you think there is a problem, but before making an objection please try the steps below and if you still think there is a problem, contact the TA that graded your homework from the email address provided in the comment section of your announced homework grade or attend the specified objection hour in your grade announcement.

<ul>

 <li>Check the comment section in the homework tab to see the problem with your homework.</li>

 <li>Download the .zip file you submitted to SUCourse and try to compile it.</li>

 <li>Check the test cases in the announcement and try them with your code. Compare your results with the given results in the announcement.</li>

</ul>

<h1>What and where to submit (IMPORTANT)</h1>




Submissions guidelines are below. Most parts of the grading process are automatic. Students are expected to strictly follow these guidelines in order to have a smooth grading process. If you do not follow these guidelines, depending on the severity of the problem created during the grading process, 5 or more penalty points are to be deducted from the grade.




<u>Add your name to the program:</u> It is a good practice to write your name and last name somewhere in the beginning program (as a comment line of course).




<u>Name your submission file:</u>

<ul>

 <li><u>Use only English alphabet letters, digits or underscore in the file names. Do not use blank,</u> <u>Turkish characters or any other special symbols or characters.</u></li>

 <li>Name your cpp file that contains your program as follows.</li>

</ul>

<h2>                                 “​ SUCourseUserName_yourLastname_yourName_HWnumber.cpp​ ”​</h2>

<ul>

 <li>Your SUCourse user name is actually your SUNet username which is used for checking sabanciuniv e-mails. Do NOT use any spaces, non-ASCII and Turkish characters in the file name. For example, if your SUCourse user name is cago, name is Çağlayan, and last name is Özbugsızkodyazaroğlu, then the file name must be:</li>

</ul>

<strong>cago_ozbugsizkodyazaroglu_caglayan_hw3.cpp</strong> ● Do not add any other character or phrase to the file name.

<ul>

 <li>Make sure that this file is the latest version of your homework program.</li>

 <li>You need to submit ALL .cpp and .h files in addition to your main.cpp in your VS solution.</li>

</ul>




<u>Submission:</u>

<ul>

 <li>Submit via SUCourse ONLY! You will receive no credits if you submit by other means</li>

</ul>

(e-mail, paper, etc.).

<ol>

 <li>Click on “Assignments” at CS300 SUCourse.</li>

 <li>Click Homework 3 in the assignments list.</li>

 <li>Click on “Add Attachments” button.</li>

 <li>Click on “Browse” button and select the zip file that you generated.</li>

 <li>Now, you have to see your zip file in the “Items to attach” list.</li>

 <li>Click on “Continue” button.</li>

 <li>Click on “Submit” button. We cannot see your homework if you do not perform this step even if you upload your file.</li>

</ol>




<u>Resubmission:</u>

<ul>

 <li>After submission, you will be able to take your homework back and resubmit. In order to resubmit, follow the following steps.

  <ol>

   <li>Click on “Assignments” at CS300 SUCourse.</li>

   <li>Click Homework 3 in the assignments list.</li>

   <li>Click on “Re-submit” button.</li>

   <li>Click on “Add/remove Attachments” button</li>

   <li>Remove the existing zip file by clicking on “remove” link. This step is very important. If you don’​ t delete the old zip file, we get both files and the old one may be graded.​</li>

   <li>Click on “Browse” button and select the new zip file that you want to resubmit.</li>

   <li>Now, you have to see your new zip file in the “Items to attach” list.</li>

   <li>Click on “Continue” button.</li>

   <li>Click on “Submit” button. We cannot see your homework if you do not perform this step even if you upload your file.</li>

  </ol></li>

</ul>