---
layout: page
title: "profile"
comments: false
sharing: true
footer: false
---

Proficient in Machine Learning and Software Engineering. Retains substantial knowledge and extensive experience of large-scaled data modeling and serving system implementation; using Python (TensorFlow, scikit-learn), Scala, and Spark (mllib) for modeling; Java for serving; Javascript, HTML, CSS, and Ruby on Rails for visualization

## Work and Internship Experiences
* #### Research Engineer, Yahoo (May 2016 – present)
	In charge of personalized stream and recommendation module, also some machine learning applications

* #### Intern, Yahoo (July 2014 – Aug 2015)
	Focused on data analytics and visualization at Yahoo. For instance, inspecting user shopping path and making complicated algorithm and results simple to understand, then presenting the work to managers to support their decision

* #### Intern, Polydice (Feb. 2013 – June 2014)
	This is a start-up creating [[iCook.tw]](http://icook.tw), the most popular recipe-sharing web in Taiwan. What I do for the company is to refine its search function and analyze customer behavior coming out with some strategies to improve user experience

* #### Intern, Trend Micro (Sep. 2013 – Jan. 2014)
	Common subgraph of virus behavior mining and visualization

## Project Experiences
* #### Unified E-Commerce Product Classification @Yahoo
	Designed a Convolutional Neural Network with better model initialization by exploiting hierarchical information. Applied transfer learning mechanism to cope with few-shot problem on other E-Commerce properties, which led to a 74% accuracy in predicting more than 2,000 categories

	{% img /images/oneec.png %}

* #### Personalized Discovery Stream @Yahoo
	Composed category and network embedding profile for millions of users in Taiwan. Applied a boosting-based model with long-term to near real-time user behavior, profile and item features, extracted by network encoding and bandit algorithm. This improved overall 25% of CTR and helps users explore more products in our E-Commerce platform

	{% img /images/stream.png %}

* #### Real Time Serving Item-based Recommender System for Taiwan and Hong-Kong E-Commerce @Yahoo
	Built up a recommender model and constructed a real-time serving system. The online CTR is three times greater than the initial model, and the average response time is under 20 ms over 300,000 products

	{% img /images/itemr12n.png %}

* #### Real Time Serving Personalized Seller Recommender System @Yahoo
	Constructed a daily-updated Alternative Least Squares Matrix Factorization model on Spark to recommend sellers to users depending on their view and follow signals

	{% img /images/sellerr12n.png %}

* #### Product Review Tagging and Ranking @Yahoo
	Tagged product comments with predefined labels by multi-label classification model using Convolutional Neural Networks and applied heuristic algorithm to have informative opinions rank higher 

	{% img /images/rnr.png %}

* #### Analysis of User Behavior on News App and Shopping Property @Yahoo
	For News App, I found some critical features attracting young users. And for Shopping Property, I analyzed key sessions where they highly possible lose their potential buyers.

	{% img /images/ec-central-app.png %}

* #### Analysis of Virus Behavior @Trend Micro (D3.js, RoR)
	To make virus examiners efficiently figure out which behaviors are the features in each cluster, I applied Likelihood Ratio (a familiar testing method for information retrieval) for feature selection. Furthermore, to help them understand the relationship between each behavior, I used Vector Space Model to find sub-graph of each cluster of virus.

	<iframe width="720" height="540" src="//www.youtube.com/embed/ZPzIiBSqHNs" frameborder="0" allowfullscreen></iframe>

* #### Analysis of User Behavior @iCook (iPython, SQL, Tornado)
	There are four main functions of the most famous recipe collection platform in Taiwan – iCook: writing recipes, making dishes after reading someone’s recipe, following someone and liking their recipes. I analyzed each function usages to help [[Polydice]](http://tw.polydice.com) the development team of iCook know better about their users. The result I discovered is that if one likes more than 30 recipes, their lifetime at iCook on average would be twice as much as those lower than 30. Besides, males writing recipes are highly possible to stay in the website longer.

	<iframe width="720" height="540" src="//www.youtube.com/embed/Hf5ic3BKs9A" frameborder="0" allowfullscreen></iframe>

* #### Search Function @iCook (ElaticSearch, RoR) [[iCook]](http://icook.tw)
	I extracted important features of recipes to refine search function. Besides, I integrated Pinyin with nGram so that the system can find the results you want even when typing the wrong Chinese characters. For example, you can find “麵包” if you search for “面包”. By our survey, the accuracy was almost 100%. For more information, You can reference [[this]](http://cytms.github.io/blog/2013/08/24/week-many-at-polydice/) to figure out the details.

* #### Crystoefl (javascript, RoR)
	To help TOEFL exam candidates to reinforce their unfamiliar research area, we collected research sources and apply K Nearest Neighbor algorithm to classify these articles so that users can choose the specific class which they’d like to study.

	<iframe width="720" height="540" src="//www.youtube.com/embed/M5oXbBbmE2s" frameborder="0" allowfullscreen></iframe>

* #### Catzuca (Objective C)
	This is an iOS APP for searching information of aboriginal culture from government and providing multimedia function for amusement. 

	<iframe width="720" height="540" src="//www.youtube.com/embed/xd8kyzKFPk0" frameborder="0" allowfullscreen></iframe>

* #### Patent Cart (javascript, RoR)
	The website is an application of Information Retrieval and Patent Analysis. We apply High Chart and D3 in the functions of statistics and citation, and use SOM tool kit to visualize patent map. 

	<iframe width="720" height="540" src="//www.youtube.com/embed/NT0w49f0QMc" frameborder="0" allowfullscreen></iframe>

* #### Parallelization of Supporting Patent Maintenance Decision (MapReduce on Hadoop)
	Every innovation protected by patent cost large amounts of maintenance fee to remain its patent legal effect, so deciding which patent to keep maintaining becomes an important issue to each company assignee. We referenced contemporary predicting approaches and found there’s a serious problem in common: flexibility of supporting decision system. Since patent number in USPTO exponentially increases annually, each prediction measurement take business unit a lot of time to build customized models to predict which patent needs to be maintained. Therefore, we applied MapReduce to paralyze measurement algorithms and made it speed-up three times more on average.

* #### Patent Clustering (Java)
	What kind of patents a company owned appeals the business strategy it might take. Hence, we applied text mining approach – group-average agglomerative clustering and labeling to figure out fields that a company focuses on. For example, Sony gets involved in not only audio device design but also system infrastructure setup, printer manufacture and multimedia detection, etc.

* #### Construction of USPTO Patent Database (Ruby, SQL)
	USPTO patents from 1976 to 2013 were parsed and maintained in our database for lab researches.

	<iframe width="720" height="540" src="//www.youtube.com/embed/D0_8JjUGr-0" frameborder="0" allowfullscreen></iframe>

* #### Tower of Hanoi (Java)
	Since the popularity of “Tower of Saviors”, we developed a Java application “Tower of Hanoi” for fun.

	<iframe width="720" height="540" src="//www.youtube.com/embed/NI2UKox1cJg" frameborder="0" allowfullscreen></iframe>

## Education
* #### Master of Information Management (Business Intelligence Lab), NTU<br>
	Courses taken: Statistical Data Analysis for Business and Management (A+), Data Mining (A+), Parallel and Distributed Programming (A), Introduction to Digital Speech Processing (A), Multimedia Analysis and Indexing (A-), Mobile Phone Programming (A+), etc.

* #### Bachelor of Information Management, NTU<br>
	Courses taken: Introduction to Information Retrieval and Text Mining (A+), Network and Platform Service Programming (A+), Data Structures (A+), Computer Organization and Structure (A+), Operating Systems (A), Database Management (A), Systems Analysis and Design (A), etc.

* #### Cloud Computing Program, Computer Science Information Engineering, NTU<br>
	Courses taken: Special Topic on Cloud Computing (A+), Cloud Computing Security (A+), etc.

## Contact Information
* Email: cytms[at]hotmail.com
* Github: github.com/cytms
* LinkedIn: [[Yu-Ting Chang]](http://www.linkedin.com/profile/view?id=144533758)