
.. default-role:: code

======================================================
        Building Websites with reStructuredText
======================================================

**Author**:*joejang@163.com*
**Source**:*pc4y.com*
**Date**:*01/12/2015*

*Abstract:A brief introduction to an aproach to implement "local-editing and remote-browsing" support for reStructuredText and Markdown documents. Related tools and techniques include reStructuredText, Markdown, Dropbox, python, php, Docutil and Pygments.*

A reStructuredText Website
==========================
Writting documents is a basic skill for most software developers. As I was using *Markdown* and *reStructuredText* for the past months, I found would be of great convenience if all documents could be translated into html automatically so that I could read the content from both the rst file and the website. What I was trying to do was typing some sentences into a file of rst or md, and then, by using some tools to help with translation, I could browse the whole page by accessing an url. What's more, I set up a dropbox sharing link between my local computer and the webserver, so whenever any bits of text were changed, the change would be almost immediately reflected on the webpage. That is, changing a local rst file means a simultaneous changing on the webpage.

Requirement
-----------

Before considering about the architecture, let's think about about the main points of this job:
        *Convenience* - Sync up local change to the remote. Use tools we can easily get on hand, Dropbox or xCloud for example.
        *Multi Format* - Convertion of Markdown and reStructuredText is available.
        AND, that's all, by now.


Overall Architecture
--------------------

.. image:: http://pc4y.com/homeres/building_websites_with_restructuredtext.png

Overall Architecture

Other Issues
============

Conversion from rst to html
---------------------------

I have tried tools like pandoc and rst2html, and both have some problems.

+------------+---------------------------------+-------------------------------------------+
| Tool       | Pros                            | Cons                                      |
+============+=================================+===========================================+
| pandoc     | Support multiple formats.       | Lack for enough default CSS templates.    |
+------------+---------------------------------+-------------------------------------------+
| rst2html   | Provide CSS templates.          | Unable to convert only body part of html. |
+------------+---------------------------------+-------------------------------------------+
| InstantRst | Instant result watching in Vim. | Inconvenient to invoke without Vim.       |
+------------+---------------------------------+-------------------------------------------+

To perform the instant coversion from rst to html, we need the help of the tool(s) mentioned above.

As we have compared the advantage and disadvantage of each tool for us, we may choose one or more tools that are most suitable for us to finish the auto-conversion job.

For this website, I used php scripts to call a rst_to_html.py to perform the conversion. 

And the rst_to_html.py is simply an encapsulation of some basic functions of Docutil and Pygments.

Conversion from markdown to html
--------------------------------

As I said that the website is going to support conversion from both reStructuredText and Markdown documents, there is the other conversion branch of Markdown using Michelf's `php-markdown <https://github.com/michelf/php-markdown>`_.

Cloud Syncing
-------------

We have many choices to support cloud syncing.

        *Dropbox, SugarSync, LiveSync...* - Multiplatform and easy-to-use.
        
        *rsync* - Command line, easy-to-use, flexible and peer-to-peer.

        *Pogoplug, xCloud* - Private cloud storage, data security, support for NAS.

        *BitTorrent Sync*

        *FTP*

Demo
====

With a few steps, this local-editing and remote-browsing website is built and convenient to use. 

The whole website is a "complished demo". Almost all the html pages in your eyes are converted from rst or md formated documents.
