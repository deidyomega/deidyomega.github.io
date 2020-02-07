---
layout: post
title: Precoders Meetup
tags:
  - meetup
  - coding
---

I gave a talk about using python virtual environements:

<section>
<h3>Python Virtual Environments</h3>
<p>
<small
>By <a href="https://mattharris.tech">Matthew Harris</a></small
>
</p>
</section>
<section>
<h3>About Me</h3>
<p>
I currently work for AnnuityCheck, a Financial Technology company.
</p>
<p>
Prior to that, I worked for the International Rescue Committee,
creating reports for the United Nations (UNHCR) and US State Dept.
</p>
</section>
<section>
<h3>What is python virtual environment</h3>
<p>A seperate python 'installation' designed to work with an individual project</p>
<p>Simular Ideas in other languages:  Node: npm, Ruby: RVM, golang: workspace, java: Maven (or many others).</p>
<p>The concept of Package Management is universal, the implmentation changes by language</p>
</section>
<section>
<h3>Major Advantages</h3>
<ul>
<li>Work on Multiple Projects without fear</li>
<li>Keep packages up to date</li>
<li>Code Sharing</li>
</ul>

<aside class="notes">
Python applications will often use packages and modules that don’t come as part of the standard library. Applications will sometimes need a specific version of a library, because the application may require that a particular bug has been fixed or the application may be written using an obsolete version of the library’s interface.<br>
<br>
This means it may not be possible for one Python installation to meet the requirements of every application. If application A needs version 1.0 of a particular module but application B needs version 2.0, then the requirements are in conflict and installing either version 1.0 or 2.0 will leave one application unable to run.<br>
<br>            
The solution for this problem is to create a virtual environment, a self-contained directory tree that contains a Python installation for a particular version of Python, plus a number of additional packages.<br>
<br>
Different applications can then use different virtual environments. To resolve the earlier example of conflicting requirements, application A can have its own virtual environment with version 1.0 installed while application B has another virtual environment with version 2.0. If application B requires a library be upgraded to version 3.0, this will not affect application A’s environment.
</aside>        
</section>
<section>
<h3>Freeze!</h3>
<p><code>pip freeze > requirements.txt</code></p>
<p>This is important, anytime you add / remove a package, refreeze</p>
<aside class="nodes">
When you commit your code to git, this allows other developers to quickly replicate the packages you used when creating your application
</aside>
</section>
<section>
<h3>How to Install (windows)</h3>
<p>Install Python (exe)</p>
<p>Fix permissions; open powershell as admin and run:</p>
<p><code>Set-ExecutionPolicy Unrestricted -Force</code></p>
</section>
<section>
<h3>How to Install (mac)</h3>
<p>Install Python (homebrew), and its auto installed!</p>
</section>
<section>
<h3>How to Install (linux)</h3>
<p><code>$ sudo apt install python3</code></p>
<p><code>$ sudo apt install python3-venv</code></p>
</section>
<section>
<h3>Live Demo!</h3>
<p>Lets create a virtual env and use it for great good</p>
<code>Win/Mac: python -m venv venv</code><br>
<code>Linux: python3 -m venv venv</code>
<hr>
<code>Win: ./venv/Script/activate</code><br>
<code>Mac/Linux: . venv/bin/activate</code>
<hr>
<code>All: deactivate</code>
</section>
<section>
<h3>Common Pitfalls</h3>
<p>Dont move the virtual env, just recreate</p>
<p>Dont commit the virtual env, be sure to add venv to .gitingore (using a standard .gitignore, it's in there)</p>
<p>Dont delete version numbers from the requirements.txt file</p>
</section>
