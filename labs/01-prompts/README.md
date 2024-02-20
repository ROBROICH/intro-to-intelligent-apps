# Prompts

In this document you will find a few exercises for practicing prompt engineering. For each exercise, you'll get some input text and then an expected completion. Your task is to write the prompt to achieve the expected completion.
___

## Exercise 1 - German Translation

**Exercise:** Write a prompt that generates the expected completion

**Input text:** 
```
I was enjoying the sun, but then a huge cloud came and covered the sky.
```
**Expected completion (or similar):** 
```
Ich genoss die Sonne, aber dann kam eine riesige Wolke und bedeckte den Himmel.
```

___

## Exercise 2 - Negation

**Exercise:** Write a prompt that generates the expected completion

**Input text:** 
```
I was enjoying the sun, but then a huge cloud came and covered the sky.
```
**Expected completion (or similar):** 
```
I was not enjoying the sun, and then a huge cloud did not come and cover the sky.
```

___

## Exercise 3 - Classification

**Exercise:** Write a prompt that generates the expected completion

**Input text:** 
```
Not much to write about here, but it does exactly what it's supposed to. filters out the pop sounds. now my recordings are much more crisp. it is one of the lowest prices pop filters on amazon so might as well buy it, they honestly work the same despite their pricing.
```
**Expected completion (or similar):**
``` 
Positive: 0.75
Neutral: 0.20
Negative: 0.05
```
___

## Exercise 4 - Start with clear instructions

**Exercise:** Tell the model the task you want it to do at the beginning of the prompt and repeat at the end so that the model generates the expected completion.

**Input text:** 
```
Your task is to verify if a statement is supported by a specific quote from the following set of snippets. 
--- 
SNIPPETS 
[1] 14 percent chance of megaquake hitting Seattle, experts say SEATTLE - There's a 14 percent chance of a magnitude 9 Cascadia earthquake hitting Seattle in the next 50 years, the U.S. Geological Survey estimates. "Unfortunately, we are unable to... 
[2] Earthquake experts lay out latest outlook for Seattle's 'Really Big One’ “We say that there's approximately a 14% chance of another approximately magnitude-9 earthquake occurring in the next 50 years,” said Erin Wirth, a geophysicist at the University of Washington... 
--- 
Is the statement "Several sources mention a chance of another large eruption" directly implied or stated by the snippets?
```
**Expected completion (or similar):**
```
No, the statement is not directly implied or stated by the snippets. The snippets mention a chance of a "megaquake" and a "magnitude 9 Cascadia earthquake" hitting Seattle in the next 50 years, but do not mention a chance of another large eruption.
```
___

## Exercise 5 - Prime the output

**Exercise:** Add phrases at the end of the prompt to obtain a model response in a desired form as shown in the expected completion.

**Task 1**

**Input text:** 
```
The future of artificial intelligence is bright. With Microsoft OpenAI, we are unlocking the potential of AI to help people achieve more. We are creating a platform that enables developers to build intelligent applications and services that can help people in their everyday lives. Our mission is to democratize AI so that everyone can benefit from its power. We are committed to advancing the state of the art in AI and making it accessible to everyone. With Microsoft OpenAI, we are taking the first steps towards a future where AI can be used to solve some of the world's most pressing challenges.
```

**Expected completion (or similar):** 
```
-Microsoft OpenAI is unlocking the potential of AI to help people achieve more. 
-The platform enables developers to build intelligent applications and services that can help people in their everyday lives. 
-The mission is to democratize AI so that everyone can benefit from its power. 
```

**Task 2**

**Input text:** 
```
John Smith is married to Lucy Smith. They have five kids, and he works as a software engineer at Microsoft. 

What search queries should I do to fact-check this?

##
```

**Expected completion (or similar):** 
```
"John Smith Microsoft software engineer" 

Another possible search query is: "Lucy Smith married to John Smith" 

A third possible search query is: "John Smith family size"
```
___

## Exercise 6 - Add clear syntax

**Exercise:** Include punctuation, headings, and section markers to help communicate intent

**Input text:** 
```
You will read a paragraph, and then issue queries to a search engine in order to fact-check it. Also explain the queries.

John Smith is married to Lucy Smith. They have five kids, and he works as a software engineer at Microsoft. What search queries should I do to fact-check this?
```

**Expected completion (or similar):** 
```
1. "John Smith Microsoft" - To check if John Smith is indeed employed at Microsoft. 
2. "John Smith Lucy Smith" - To check if John Smith is married to Lucy Smith. 
3. "John Smith children" - To check if John Smith has five children
```

**Note**: If you’re not sure what syntax to use, consider using markdown or XML, since LLMs have been trained on a lot of web content in XML or markdown

___

## Exercise 7 - Prompt Chaining

Prompt chaining is a technique that involves concatenating several prompts to create a more complex prompt that directs the model towards specific outputs. This technique is powerful for prompt engineering because it enables the creation of a more focused prompt that provides the model with more specific information to generate an output. By chaining prompts, the model is directed to focus on specific aspects of the task or problem at hand, improving the accuracy and relevance of the generated outputs. 

***Exercise:** Follow the steps to build a prompt chain

**Step 1** Entity Extraction

**Input text:** 
``` 
Please extract entities as JSON with fields text, type from the following news article: 'The new iPhone model is set to be released next month. It has been highly anticipated by Apple fans and is expected to feature a larger screen and improved camera'

Avoid any irrelevant information and focus on listing only the entities.
```
**Expected completion (or similar):** 
```
{"entities": [{"text": "iPhone", "type": "Product"},{"text": "Apple","type": "Organization"}]}  
```
**Step 2** Summarization (paste the output from Step 1 as input to Step 2)

**Input text:** 
``` 
Please summarize the information about the product 
{"entities": [{"text": "iPhone", "type": "Product"},{"text": "Apple","type": "Organization"}]}  
```
**Expected completion (or similar):** 
```
The iPhone is a product developed and sold by Apple. It is a line of smartphones known for their sleek design, advanced technology, and integration with the Apple ecosystem. The iPhone has various models and features, and it is one of the most popular smartphones in the world.
```
**Step 3** Sentiment Analysis (paste the output from Step 2 as input to Step 3)

**Input text:** 
``` 
Please provide a sentiment for the following text: 
The iPhone is a product developed and sold by Apple. It is a line of smartphones known for their sleek design, advanced technology, and integration with the Apple ecosystem. The iPhone has various models and features, and it is one of the most popular smartphones in the world.
```
**Expected completion (or similar):** 
```
The sentiment of the text is positive, expressing admiration for the iPhone's sleek design, advanced technology, and popularity.
```
___

## Exercise 8 - Few-shot learning
Also known as in-context learning, it allows the model to interact with new knowledge.

**Exercise:** Execute the input text with the few-shot learning prompt to generate the expected completion.

**Input text:** 
```
Write a list of puns.

1. "Why did Adele cross the road? To say hello from the other side."

2. "What kind of concert only costs 45 cents? A 50 Cent concert featuring Nickelback."

3. "What did the grape say when it got crushed? Nothing, it just let out a little wine."

4. "What was Forrest Gump's email password? 1forrest1"

5. "Can February March? No, but April May."

6. "What do you call fancy language model?

```

Expected completion: 
```
What do you call a fancy language model? A lexiconnoisseur.
```

___

## Exercise 9 - Few-shot reasoning

Few-shot reasoning is similar to few-shot prompt but instead here we provide an reasoning example for a specific task to help the model reason on a different task. For example here, if ask the model to answer a simple logical reasoning task, it fails, but if we provide the model with a similar logical reasoning example , it shows the model how it can solve for a different similar logical task.

**Exercise:** In input text, modify the answer example to provide the model with a similar logical reasoning example so as a result the model understand the mechanism needed to solve for the new problem. 

**Input text:** 
```
Roger has 5 tennis balls. He buys 2 more cans of tennis balls. Each can has 3 tennis balls. How many tennis balls does he have now?

Answer: The answer is 11.

The cafeteria has 23 apples. If they used 20 to make lunch and bought 6 more, how many do they have?
```

**Expected completion (or similar):** 
``` 
The cafeteria had 23 apples originally. They used 20 to make lunch. So they had 23-20 = 3. They bought 6 more apples, so they have 3 + 6 = 9. The answer is 9
```
___

## Exercise 10 - Guardrails

You can use meta-prompts / system prompts to provide guardrails to the models output. In this example here , if we ask the model what is cosmos, it replies that cosmos is open-source blockchain decentralized network. This is not the answer that we wanted. 

**Excercise:** Provide a system message in addition to the prompt, telling the model that we only want specific information on Microsoft products.

**Input text:** 
``` 
What is Cosmos?
```

**Expected completion (or similar):** 
```
Cosmos is a globally distributed, multi-model database service designed to provide highly responsive and scalable data storage and querying capabilities for modern applications. It is offered by Microsoft as Azure Cosmos DB, which is a fully managed, multi-model database service for building globally distributed applications. 😊 
```

## Exercise 11 - Use affordances/tools when needed

LLMs often perform better if the task is broken down into smaller step

**Exercise:** Execute the input text and validate by using LLM if the claims are supported by the search results. 

**Input text:** 
```
You will read a paragraph, extract factual claims, and then use search engine results to fact-check them
---
PARAGRAPH
John Smith is married to Lucy Smith. They have five kids, and he works as a software engineer at Microsoft. What search queries should I do to fact-check this?
---
FACTUAL CLAIMS
- John Smith is married to Lucy Smith
- John and Lucy have five kids
- John works as a software engineer at Microsoft
---
Here are various search queries issued to research the claims above:
SEARCH QUERIES
- John Smith married to Lucy Smith
- John Smith number of children
- John Smith software engineer Microsoft
---
Here are snippets of the search results:
SNIPPETS:
[1] … John Smith’s wedding was on September 25, 2012 …
[2] … John Smith was accompanied by his wife Lucy to a ball
[3] John was accompanied to the soccer game by his two daughters and three Sons
[4] … After spending 10 years at Microsoft, Smith founded his own startup, LIKELUS
---
Given the snippets, fact check each of the factual claims above:
```

**Expected completion (or similar):** 
```
- John Smith is married to Lucy Smith: Confirmed. Snippet [1] and [2] both mention John Smith's wife as Lucy. 

- John and Lucy have five kids: Confirmed. Snippet [3] mentions that John was accompanied by his two daughters and three sons. 

- John works as a software engineer at Microsoft: Partially confirmed. Snippet [4] mentions that John spent 10 years at Microsoft, but it does not explicitly state that he currently works there. Further research may be needed to confirm his current employment status
```
___

## Exercise 12 - Chain of thought prompting

**Exercise:** Instruct model to proceed step-by-step and present all the steps involved to generate the expected completion.

**Input text:** 
``` 
Who was the most decorated (maximum medals) individual athlete in the Olympic games that were held at Sydney? 
```

**Expected completion (or similar):** 
```
Step 1: Researching the most decorated individual athlete in the Olympic games that were held at Sydney 

Step 2: According to the Sydney 2000 Olympic Games official website, the most decorated individual athlete in the Olympic games that were held at Sydney was Ian Thorpe from Australia. He won five medals (three gold and two silver) in swimming events. 

Step 3: According to the International Olympic Committee, Thorpe was the most decorated individual athlete in the Olympic games that were held at Sydney. Answer: Ian Thorpe
```
___

## Exercise 13 - Use quotes to generate a single sentence

If the desired model response is only a single simple sentence or string use stop sequences

**Exercise:** Write a prompt that generates the expected completion statement

**Input text:** 
``` 
Please rewrite the following sentence in a more concise manner  
---  

SENTENCE: Lucy is a mother of two, who lives in Chicago with her husband 

and two children, and practices law at Junior & Co.  

---  
```

**Expected completion (or similar):** 
```
Lucy, a mother of two living in Chicago with her husband and children, practices law at Junior & Co  
```

## Exercise 14 - Specifying output structure

Reduce the prevalence of made-up response by specifying the structure of the output

**Exercise:** Write a prompt that generates the expected completion statement

**Input text:** 
``` 
Cluster the following news headlines into topic categories based on patterns seen within the text. Also mention reasoning behind how these categories were defined. {"TOPIC_NAME": "Artificial Intelligence and Machine Learning", "HEADLINES": ["From books to presentations in 10s with AR + ML",

Input news headlines: 
1. "From books to presentations in 10s with AR + ML" 
2. "Demo from 1993 of 32-year-old Yann LeCun showing off the World's first Convolutional Network for Text Recognition" 
3. "First Order Motion Model applied to animate paintings" 
4. "Robinhood and other brokers literally blocking purchase of $GME, $NOK, $BB, $AMC; allow sells" 
5. "United Airlines stock down over 5% premarket trading" 6. "Bitcoin was nearly $20,000 a year ago today" 
```

**Expected completion (or similar):** 
``` json
{
  "TOPIC_NAME": "Artificial Intelligence and Machine Learning",
  "HEADLINES": [
  "From books to presentations in 10s with AR + ML",
  "Demo from 1993 of 32-year-old Yann LeCun showing off the World's first Convolutional Network for Text Recognition",
  "First Order Motion Model applied to animate paintings"
  ],
  "REASONING": "The headlines mention advancements and applications of artificial intelligence and machine learning, such as using AR and ML for quick presentations, demonstrating the first Convolutional Network for Text Recognition, and applying the First Order Motion Model to animate paintings."
}
```

## Exercise 15 - NL to SQL with Codex

**Exercise:** Write a prompt that generates a query that returns the top 10 orders and show the customer name

**Input text:** 
```
Table information:
* Table: customer // Columns: firstname, name, customer_id, address
* Table: orders // Columns: order_id, customer_id, product_id, product_amount
* Table: products // Columns: product_id, price, name, description
```
**Expected completion (or similar):** 
``` SQL
SELECT c.firstname, c.name AS lastname, p.name AS product_name, SUM(o.product_amount) AS total_amount  
FROM orders o  
JOIN customer c ON o.customer_id = c.customer_id  
JOIN products p ON o.product_id = p.product_id  
GROUP BY o.product_id  
ORDER BY total_amount DESC  
LIMIT 10; 
  ```


## Exercise 16 - Adjusting 'Temperature' and 'Top_P' parameters

**Exercise:** Execute the input text with first temperature set to 0.1 and then set it to 0.9 . Observe how the change of temperature influences the output.

**Input text:** 
``` 
Write a product launch email for new AI-powered headphones that are priced at $79.99 and available at Best Buy, Target and Amazon.com. The target audience is tech-savvy music lovers and the tone is friendly and exciting.

1. What should be the subject line of the email? 
2. What should be the body of the email?  
```

## Next Section

📣 [Integrating AI](../02-integrating-ai/README.md)
