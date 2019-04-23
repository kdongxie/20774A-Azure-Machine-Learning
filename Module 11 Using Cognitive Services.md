# Module 11 Using Cognitive Services

## Module Overview

- Cognitive Services overview
- Processing language
- Processing image and video



## Lesson 1: [Cognitive Services overview](<https://azure.microsoft.com/ko-kr/services/cognitive-services/>)
- What is a cognitive service?
- Customer scenarios

### What is a cognitive service?

Cognitive Services:

- **Vision**. Analyze photos and videos

- **Speech**. Convert speech to text and text to speech

- **Language**. Understand intent from language

- **Search**. Find information on the web using Bing

### Customer scenarios

- Uber driver identification
- Starship Commander voice control



## Lesson 2: Processing language

- Language
- Learning to talk
- Using language to make decisions
- Demonstration: Using curl and Microsoft Kiosk with Language APIs



### Language

- **Natural Language Processing [NLP]**
- Part of speech
  - Nouns
  - Adjectives
  - Verbs

- Tokens
  - The yellow fox can’t jump = The – yellow – fox – can –’t –jump

### Learning to talk

- **Bing Spell Check** : 잘못된 Spell 을 찾아 준다. 
- Linguistic analysis
- Text analysis
- Translator
- WebLM

### Using language to make decisions

- Utterances are translated to intents
- Intents drive app decisions
- Entities describe information about the intent
- Features help identify intents and entities

### Demonstration: Using curl and Microsoft <u>Kiosk</u> with Language APIs
In this demonstration, you will see how to:

- Use the Cognitive Services Text Analytics API with curl commands
- Use the Cognitive Services Bing Search API with the Kiosk application

## Lesson 3: Processing image and video
- Face
- Emotion
- Content moderator
- Video
- Computer Vision
- Demonstration: Using Microsoft Kiosk with Image and Video APIs



### Face

- Person and person groups
- Face detection
- Face verification
- Face identification
- Similar face searching
- Face grouping

### Emotion

```
 "faceRectangle": {
      "left": 488,
      "top": 263,
      "width": 148,
      "height": 148
    },
    "scores": {
      "anger": 9.075572e-13,
      "contempt": 7.048959e-9,
      "disgust": 1.02152783e-11,
      "fear": 1.778957e-14,
      "happiness": 0.9999999,
      "neutral": 1.31694478e-7,
      "sadness": 6.04054263e-12,
      "surprise": 3.92249462e-11
    }
```

![image](https://user-images.githubusercontent.com/46669551/56486516-cb87c480-6512-11e9-8429-3d707bca421a.png)

### Content moderator

- Automated
- Human
- Hybrid
- Content Moderator UI
- Image moderation
- Text Moderation

### Video

- Face detection and tracking
- Motion detection
- Stabilization
- Video thumbnail

### Computer Vision

- Computer Vision
- Tagging images
- Categorizing images
- Generating descriptions

### Demonstration: Using Microsoft Kiosk with Image and Video APIs
In this demonstration, you will see how to: 

- Configure the Kiosk application to use Microsoft Cognitive Services’ Face, Emotion, and Computer Vision APIs
- Use the Kiosk application to detect faces and facial expressions

## Lab: [Using Cognitive Services](<https://docs.microsoft.com/ko-kr/windows/wsl/install-win10?f=255&MSPPError=-2147217396>)

- Exercise 1: Build a language application
- Exercise 2: Build a face detection application

[LUIS](<https://www.luis.ai/home>) : work book의  Senario 와 LUIS의 Version이 달라 수행하기 힘듬.



> Lab Scenario
>
> You work as a data scientist for Adatum Consultant	s, a company that provides machine learning services and advice for a range of clients. One of your clients is planning the deployment of a range of applications that use of the Cognitive Services APIs.
>
> You are working with a team of business analysts and developers, and are focusing on the following scenarios:
>
> - Building a hotel bot for hotel reviews and searches, utilizing LUIS
> - Using the Face API to analyze photos

>Lab Review
>
>- In exercise 1, does the Cognitive Services LUIS search Bing for hotel reviews?