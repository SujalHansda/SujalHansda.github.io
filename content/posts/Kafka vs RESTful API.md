+++
title = "Why use Kafka"
date = 2023-06-10
[taxonomies]
tags = ["kafka", "api"]
authors = ["Sujal Hansda"] 
+++
<img src="https://svn.apache.org/repos/asf/kafka/site/logos/originals/png/WIDE%20-%20Black%20on%20Transparent.png" alt="Image" style="width: 60%;">

When I was an intern, a senior developer assigned me to implement kafka in microservices.
At first I thought of it as a usual library that automate something. Kafka is a messaging service used to communicate between microservices. But the catch was, I have already implemented communication using Feign Client ( used in Spring Boot microservices). I used to call endpoints of other microservices to fetch and modify data. So what's the benefit of using Kafka. This ticked my mind for a while but after spending time on fourms and documentations I finally understood.

| Kafka                                                                                                                     | REST                                                                                                                                                                                            |
|---------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Publish & Subscribe (just process the pipeline, will notify once the job is done)                                         | Request & Await response (on-demand)                                                                                                                                                            |
| Publish once - Subscribe n times (by n components)                                                                        | Request once, get the response once. Deal over                                                                                                                                                  |
| Data is stored in topic. Seek back & forth (offsets) whenever you want till the topic is retained                         | Once the response is over, it is over. Manually employ a database to store the processed data                                                                                                   |
| The one who makes the request typically is not interested in a response (except the response that if the message is sent) | I am making the request means I typically expect a response (not just a response that you have received the request, but something that is meaningful to me, some computed result for example!) |