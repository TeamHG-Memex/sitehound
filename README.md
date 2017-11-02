# Site Hound
Site Hound (previously THH) is a Domain Discovery Tool that extends the capabilities of commercial search engines using automation and human-in-the-loop (HITL) machine learning, allowing the user efficiently expand the set of relevant web pages within his domain/s or topic/s of interest. <br>
Site Hound is the UI to a more complex set of tools described below.
Site Hound was developed under the Memex Program by HyperionGray LLC in partnership with Scrapinghub, Ltd. (2015/2017)

### Main Features

 1. Role Based Access Control (RBAC).
 2. Multiple __workspaces__ for keeping things tidy.
 3. Input of __keywords__, to be included or excluded to the search.
 4. Input of __seeds URLs__, an initial list of websites that you already know are on-topic.
 5. Expand the list of sites by fetching the keywords on multiple commercial search engines.
 6. Displays __screenshots__ (powered by Splash), title, text, html, relevant terms in the text 
 7. Allows the user to __iteratively train__ a topic model based on these results by assigning them into defined values (Relevant/Irrelevant/Neutral), as well as re-scoring the associated keywords.
 8. Allows an unbounded training module based on __user-defined categories__.
 9. __Language detection__ (powered byApache Tika) and __page-type classification__
10. Allows the user to view the trained topic model through a human-interpretable explaination of the model powered by our machine learning explanation toolkit [ELI5](https://github.com/TeamHG-Memex/eli5)
11. Performs a __broad crawl__ of thousand of sites, using __Machine Learning__ provided by [DeepDeep-crawler](https://github.com/TeamHG-Memex/hh-deep-deep) filtering the ones matching the defined domain.
12. Displays the results in an interface similar to __Pinterest__ for easy scrolling of the findings.
13. Provides __summarized__ data about the broad crawl and __exporting__ of the broad-crawl results in CSV format.
14. Provides real time information about the __progress__ of the crawlers.
15. Allows search of the Dark web via integration with an __onion index__ 

   
    
### Infrastructure Components

When the app starts up, it will try to connect first with all this components    
- Mongo (>3.0.*) stores the data about users, workspace and metadata about the crawlings 
- Elasticsearch (2.0) stores the results of the crawling (screenshots, html, extracted text)
- Kafka (10.1.*) handles the communication between the backend components regarding the crawlings.

Custom Docker versions of these components are provided with their extra args to set up the stack correctly, in the Containers section below. 
    

### Service Components:

This components offer a suite of capabilities to Site Hound. Only the first three components are required.

- [Sitehound-Frontend](https://github.com/TeamHG-Memex/sitehound-frontend): Performs queries on the Search engines, follows the relevant links and orchestrates the 
- [Sitehound-Backend](https://github.com/TeamHG-Memex/sitehound-backend): Performs queries on the Search engines, follows the relevant links and orchestrates the screenshots, text extraction, 
language identification, page-classification, naive scoring using the cosine difference of TF*IDF, and stores the results sets.<br>
- [Splash](https://github.com/scrapinghub/splash): Splash is used for screenshoot and html capturing.
- [HH-DeepDeep](https://github.com/TeamHG-Memex/hh-deep-deep): Allows the user to train a page model to perform on-topic crawls
- [ExcavaTor]: Our own tor index. This is currently a private db. Ask us about it!


Here is the components diagram for reference
![Components Diagram](img/Sitehound-architecture-diagram.png)

### Install:

Check the [installation guide](installation/README.md)

### How to use it:

Check the [walkthrough guide](user-docs/sitehound-walkthrough-guide_October-2017_v2)
