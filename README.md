# Logging-Best-Practices-Application-Level-Logging

Logs from the application level are the only way your application talks back to you. Having proper logs with commendable search capabilities is like having a torch in a dark room.

Fully exploiting logs in case of any issues is very underrated. We as software engineers can utilize logs from the application to resolve issues as well as know the general health of the application.

````
Logs can be instrumental to profile application performance too.
````

This post is focused on best practices you can follow when logging from the application level and how it can help you as a software engineer.

# Best practices at a glace
Following are the main best practices for logging:

## 1. Log information optimally
Too much information is noise and too less information is inadequate. It is difficult to strike the balance of how much log is optimal but that is the challenge. In the case of microservices also think about traceability between services like using a unique request identifier. Another thing to keep in mind is logs are temporal, not permanent. As they are not stored in the database they usually have a life from some days to some weeks.

## 2. Always follow severity levels
An emergency means your on-call phone is going to ring at 2 AM in the morning but an info severity is something that won’t bother anyone. You have to agree as a team on some set standards like the syslog one.

## 3. Structure your logs
Have a structure in your log lines, like have a message and a context array to add more information about the message. Follow an agreed upon JSON standard for logging. This makes it easy to parse and search. You could even set more rules like the date is mandatory, a description cannot be more than 255 characters, extra information goes in the context. Having these simple rules makes it easier to find the log when in need. It is highly recommended to provide context with log lines like add the details of the order (things that are not sensitive of course) when logging that the order could not be shipped for instance.

## 4. Write logs carefully (don’t hamper performance)
Make sure that adding logs does not add a lot of extra milliseconds to your response times. As far as possible write logs in an async way, logs could even be written locally in a log file and shipped using a log shipper to the service of your choice. You can also make use of tried and trusted library depending on the language/framework you are working with. Using queues could also be an option to ship logs but keep in mind the possible lag when viewing logs.

## 5. Use the right tools for the job
The tools and services you choose to ship, view, search and sort logs are your team’s choice. Depending on the budget, the appetite for using external services a team could use a fully self-managed stack like [ELK](https://www.elastic.co/elk-stack)/[Graylog](https://www.graylog.org/) or go full SAAS with services like [Logentries](https://logentries.com/)/[Sematext Logsense](https://sematext.com/logsene/). The main idea is to use the tools that fit your needs very efficiently. If you need almost real-time logs using a queue, for instance, might not be the best decision. So design your logging infrastructure and stack that fits your needs well.

## Conclusion
````
If a dog is a man’s best friend, logs are software engineer’s best friend.
````

Use logs to the fullest to get the most out of it and keep in mind the best practices about logging.
