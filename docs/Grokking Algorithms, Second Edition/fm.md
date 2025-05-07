---
sidebar_position: 7
---

# Front matter

## foreword

More people than ever need to learn how to program. Sure, some people literally program for their jobs (software engineers or web developers, for example). But many other jobs, not historically requiring programming, have a programming component now or will in the future. Programming also helps people understand the technological world in which they live.

Unfortunately, the benefits of programming are not equally distributed. In North American computer science (CS) programs, for example, we have a very low participation of women and some ethnic/racial groups. It’s critical that we be able to expand programming and CS to a more diverse group. The solution will involve making progress on a number of fronts, including overcoming bias, training more teachers, and offering more diversified learning experiences. We need to help more people “get in.”

I’m excited about Bhargava’s book because it offers a new way to get into algorithms, which is a key component of effective programming. Some people will tell you that there’s only one way to learn algorithms: find a dense mathematical book about algorithms, read it, and, like, understand everything. But that privileges the types of people who can learn that way, who have time to learn that way, and who need to learn that way in the first place. It also assumes that we know *why* someone wants to learn algorithms, which, let’s face it, is not a fair assumption to make.

To be clear, some of my favorite CS books are exactly those kinds of mathematically oriented algorithms books. Those books work for me. They work for a lot of CS professors. But maybe that’s the problem: it’s too easy to assume that the way we learn is the same way that others learn. What we need are all kinds of learning resources about all kinds of CS topics, each designed for a particular audience.

Bhargava’s book is intentionally designed for people who want a nonmathematical introduction to algorithms. What impresses me most here is not what Bhargava chose to include but what he chose *not* to include. You can’t include everything in a book like this—that would be overwhelming and is not the point.

Bhargava’s teaching expertise enables him to wring a lot of teaching out of not a lot of pages. In reading the “Dynamic Programming” chapter, for example, I was struck by the care with which Bhargava answers a lot of anticipated reader questions that other algorithm books would not answer.

I hope that this book helps you learn, whether you’re trying algorithms for the first time or you’ve struggled to find the right resource until now. Happy Grokking!

—Daniel Zingaro, University of Toronto

## preface

I first got into programming as a hobby. *Visual Basic 6 for Dummies* taught me the basics, and I kept reading books to learn more. But the subject of algorithms was impenetrable for me. I remember savoring the table of contents of my first algorithms book, thinking “I’m finally going to understand these topics!” But it was dense stuff, and I gave up after a few weeks. It wasn’t until I had my first good algorithms professor that I realized how simple and elegant these ideas were.

I wrote my first illustrated blog post back in 2012. I’m a visual learner, and I really liked the illustrated style. Since then, I’ve written a few illustrated posts on functional programming, Git, machine learning, and concurrency. By the way, I was a mediocre writer when I started out. Explaining technical concepts is hard. Coming up with good examples takes time, and explaining a difficult concept takes time. So it’s easiest to gloss over the hard stuff. I thought I was doing a pretty good job until after one of my posts got popular, a coworker came up to me and said, “I read your post, and I still don’t understand this.” I still had a lot to learn about writing.

Somewhere in the middle of writing these blog posts, Manning reached out to me and asked if I wanted to write an illustrated book. Well, it turns out that Manning editors know a lot about explaining technical concepts, and they taught me how to teach. I wrote this book to scratch a particular itch: I wanted to write a book that explained hard technical topics well, and I wanted an easy-to-read algorithms book.

The first edition of this book came out in 2016. Since then, more than 100,000 people have read this book. I’m delighted to see how many people have connected with the visual learning style.

With this second edition, my goal remains the same. In this book, I use illustrations and memorable examples to make concepts stick. The book is designed for readers who know how to code and want to learn more about algorithms without any math knowledge required.

The second edition fills some gaps in the first edition. I heard from a lot of readers that they wanted me to explain trees. There are now two chapters on trees in this book. I have also expanded the section on NP completeness. NP-complete is a very abstract concept, and I wanted an explanation that would make it more concrete. If you feel the same way, I hope the section on NP-complete fills that gap for you.

My writing has come a long way since that first blog post, and I hope you find this book an easy and informative read.

## acknowledgments

Kudos to Manning for giving me the chance to write this book and letting me have a lot of creative freedom with it. Thanks to publisher Marjan Bace, Mike Stephens for getting me on board, and Ian Hough for being an incredibly responsive and helpful editor. Thanks also to the people on Manning’s production team: Paul Wells, Debbie Holmgren, and all the others behind the scenes. In addition, I want to thank the many people who read the manuscript and offered suggestions: Daniel Zingaro, Ben Vinegar, Alexander Manning, and Maggie Wenger. Thanks to David Eisenstat, my technical reviewer, and Tony Holdroyd, the Manning technical proofreader, for catching my many errors.

Thanks to the people who helped me reach this point: Bert Bates for teaching me how to write; the folks on the Flashkit game board for teaching me how to code; the many friends who helped by reviewing chapters, giving advice, and letting me try out different explanations, including Ben Vinegar, Karl Puzon, Alex Manning, Esther Chan, Anish Bhatt, Michael Glass, Nikrad Mahdi, Charles Lee, Jared Friedman, Hema Manickavasagam, Hari Raja, Murali Gudipati, Srinivas Varadan, and others, and Gerry Brady for teaching me algorithms. Another big thank you to algorithms academics like CLRS, Knuth, and Strang. I’m truly standing on the shoulders of giants.

Dad, Mom, Priyanka, and the rest of the family: thank you for your constant support. And a big thank you to my wife Maggie, and my son Yogi. There are many adventures ahead of us, and some of them don’t involve staying inside on a Friday night rewriting paragraphs.

To all the reviewers—Abhishek Koserwal, Alex Lucas, Andres Sacco, Arun Saha, Becky Huett, Cesar Augusto Orozco Manotas, Christian Sutton, Diógines Goldoni, Dirk Gómez, Ed Bacher, Eder Andres Avila Niño, Frans Oilinki, Ganesh Swaminathan, Giampiero Granatella, Glen Yu, Greg Kreiter, Javid Asgarov, João Ferreira, Jobinesh Purushothaman, Joe Cuevas, Josh McAdams, Krishna Anipindi, Krzysztof Kamyczek, Kyrylo Kalinichenko, Lakshminarayanan AS, Laud Bentil, Matteo Battista, Mikael Byström, Nick Rakochy, Ninoslav Cerkez, Oliver Korten, Ooi Kuan San, Pablo Varela, Patrick Regan, Patrick Wanjau, Philipp Konrad, Piotr Pindel, Rajesh Mohanan, Ranjit Sahai, Rohini Uppuluri, Roman Levchenko, Sambaran Hazra, Seth MacPherson, Shankar Swamy, Srihari Sridharan, Tobias Kopf, Vivek Veerappan, William Jamir Silva, and Xiangbo Mao—your suggestions helped make this a better book.

Finally, a big thank you to all the readers who took a chance on this book, and the readers who gave me feedback in the book’s forum. You really helped make this book better.

## about this book

*Grokking Algorithms* is designed to be easy to follow. I avoid big leaps of thought. Any time a new concept is introduced, I explain it right away or tell you when I’ll explain it. Core concepts are reinforced with exercises and multiple explanations so that you can check your assumptions and make sure you’re following along.

I lead with examples. Instead of writing symbol soup, my goal is to make it easy for you to visualize these concepts. I also think we learn best by being able to recall something we already know, and examples make recall easier. So when you’re trying to remember the difference between arrays and linked lists (explained in chapter 2), you can just think about getting seated for a movie. Also, at the risk of stating the obvious, I’m a visual learner. This book is chock-full of images.

The contents of the book are carefully curated. There’s no need to write a book that covers every sorting algorithm—that’s why we have Wikipedia and Khan Academy. All the algorithms I’ve included are practical. I’ve found them useful in my job as a software engineer, and they provide a good foundation for more complex topics. Happy reading!

How to use this book

The order and contents of this book have been carefully designed. If you’re interested in a topic, feel free to jump ahead. Otherwise, read the chapters in order—they build on each other.

I strongly recommend executing the code for the examples yourself. I can’t stress this part enough. Just type out my code samples verbatim (or download them from [https://www.manning.com/books/grokking-algorithms-second-edition](https://www.manning.com/books/grokking-algorithms-second-edition) or [https://github.com/egonschiele/grokking\_algorithms](https://github.com/egonschiele/grokking_algorithms)) and execute them. You’ll retain a lot more if you do.

I also recommend doing the exercises in this book. The exercises are short—usually just a minute or two, sometimes 5 to 10 minutes. They will help you check your thinking, so you’ll know when you’re off track before you’ve gone too far.

Who should read this book?

This book is aimed at anyone who knows the basics of coding and wants to understand algorithms. Maybe you already have a coding problem and are trying to find an algorithmic solution. Or maybe you want to understand what algorithms are useful for. Here’s a short, incomplete list of people who will probably find this book useful:

- Hobbyist coders
- Coding boot camp students
- Computer science grads looking for a refresher
- Physics/math/other grads who are interested in programming

How this book is organized: A roadmap

The first three chapters of this book lay the foundations:

- *Chapter 1*—You’ll learn your first practical algorithm: binary search. You also learn to analyze the speed of an algorithm using big O notation. Big O notation is used throughout the book to analyze how slow or fast an algorithm is.
- *Chapter 2*—You’ll learn about two fundamental data structures: arrays and linked lists. These data structures are used throughout the book, and they’re used to make more advanced data structures like hash tables (chapter 5).
- *Chapter 3*—You’ll learn about recursion, a handy technique used by many algorithms (such as quicksort, covered in chapter 4).

In my experience, big O notation and recursion are challenging topics for beginners. So I’ve slowed down and spent extra time on these sections.

The rest of the book presents algorithms with broad applications:

- *Problem-solving techniques*—Covered in chapters 4, 10, and 11. If you come across a problem and aren’t sure how to solve it efficiently, try divide and conquer (chapter 4) or dynamic programming (chapter 11). Or you may realize there’s no efficient solution, and get an approximate answer using a greedy algorithm instead (chapter 10).
- *Hash tables*—Covered in chapter 5. A hash table is a very useful data structure. It contains sets of key and value pairs, like a person’s name and their email address or a username and the associated password. It’s hard to overstate hash tables’ usefulness. When I want to solve a problem, the two plans of attack I start with are “Can I use a hash table?” and “Can I model this as a graph?”
- *Graph and tree algorithms*—Covered in chapters 6, 7, 8, and 9. Graphs are a way to model a network: a social network, or a network of roads, or neurons, or any other set of connections. Breadth-first search (chapter 6) and Dijkstra’s algorithm (chapter 9) are ways to find the shortest distance between two points in a network: you can use this approach to calculate the degrees of separation between two people or the shortest route to a destination. Trees are a type of graph. They are used in databases (often B-trees), in your browser (the DOM tree), or in your file system.
- *K-nearest neighbors (KNN)*—Covered in chapter 12. This is a simple machine-learning algorithm. You can use KNN to build a recommendations system, an OCR engine, a system to predict stock values—anything that involves predicting a value (“We think Adit will rate this movie 4 stars”) or classifying an object (“That letter is a Q”).
- *Next steps*—Chapter 13 goes over more algorithms that would make good further reading.

About the code

All the code examples in this book use Python 3. All code in the book is presented in a `fixed-width font like this` to separate it from ordinary text. Code annotations accompany some of the listings, highlighting important concepts.

You can get executable snippets of code from the liveBook (online) version of this book at [https://livebook.manning.com/book/grokking-algorithms-second-edition](https://livebook.manning.com/book/grokking-algorithms-second-edition). The complete code for the examples in the book is available for download from the Manning website at [www.manning.com](https://www.manning.com) and from [https://github.com/egonschiele/grokking\_algorithms](https://github.com/egonschiele/grokking_algorithms).

I believe you learn best when you really enjoy learning—so have fun and run the code samples!

liveBook discussion forum

Purchase of *Grokking Algorithms* includes free access to liveBook, Manning’s online reading platform. Using liveBook’s exclusive discussion features, you can attach comments to the book globally or to specific sections or paragraphs. It’s a snap to make notes for yourself, ask and answer technical questions, and receive help from the author and other users. To access the forum, go to [https://livebook.manning.com/book/grokking-algorithms-second-edition](https://livebook.manning.com/book/grokking-algorithms-second-edition). You can also learn more about Manning’s forums and the rules of conduct at [https://livebook.manning.com/discussion](https://livebook.manning.com/discussion).

Manning’s commitment to our readers is to provide a venue where a meaningful dialogue between individual readers and between readers and the author can take place. It is not a commitment to any specific amount of participation on the part of the author, whose contribution to the forum remains voluntary (and unpaid). We suggest you try asking the author some challenging questions lest their interest stray! The forum and the archives of previous discussions will be accessible from the publisher’s website for as long as the book is in print.

## about the author

![](assets/image_Bhargava.png)

Aditya Bhargava is a software engineer. He has a master’s degree in computer science from the University of Chicago. He also runs a popular illustrated tech blog at adit.io.

About the technical editor

David Eisenstat is a research software engineer. He holds a PhD in Computer Science from Brown University.
