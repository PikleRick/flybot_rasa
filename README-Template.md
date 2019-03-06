# Flybot - Tourism Chatbot

The goal here is to make you familiar with the technicalities regarding the chatbot, so it can extract the right entities and the right intent.

## Getting Started

Start by getting a local copy of the project for development and testing purposes.

### Prerequisites

First, you have to install python 3 or later.

```
Give examples
```

### Installing

We are using in this projects, among other python libraries, the rasa_nlu library (wich is responsible of training our entity/intent recognition model). To install those libraries, open a shell and tape the following:


```
$ pip install -r requirements.txt
```

And repeat


```
until finished
```

End with an example of getting some data out of the system or using it for a little demo







## Presenting the rasa_nlu library

Rasa NLU is an open-source tool for intent classification and entity extraction. For example, taking a sentence like

```
"I am looking for a Mexican restaurant in the center of town"
```
and returning structured data like

```
{
  "intent": {
    "confidence": 0.9998878932233402,
    "name": "flight_search"
  },
  "intent_ranking": [
    {
      "confidence": 0.9998878932233402,
      "name": "flight_search"
    },
    {
      "confidence": 0.00010302332102096702,
      "name": "negative"
    },
    {
      "confidence": 8.601318306999593e-06,
      "name": "greet"
    },
    {
      "confidence": 3.149591201931632e-07,
      "name": "bye"
    },
    {
      "confidence": 1.6717821163472018e-07,
      "name": "affirmative"
    }
  ],
  "entities": [
    {
      "confidence": 0.9992337253580568,
      "extractor": "ner_crf",
      "end": 25,
      "start": 17,
      "value": "toulouse",
      "entity": "origin"
    },
    {
      "confidence": 0.9920121427732627,
      "extractor": "ner_crf",
      "end": 33,
      "start": 28,
      "value": "paris",
      "entity": "destination"
    },
    {
      "extractor": "ner_duckling_http",
      "text": "ce weekend",
      "start": 34,
      "value": {
        "from": "2019-03-08T18:00:00.000+01:00",
        "to": "2019-03-11T00:00:00.000+01:00"
      },
      "additional_info": {
        "values": [
          {
            "from": {
              "value": "2019-03-08T18:00:00.000+01:00",
              "grain": "hour"
            },
            "type": "interval",
            "to": {
              "value": "2019-03-11T00:00:00.000+01:00",
              "grain": "hour"
            }
          }
        ],
        "from": {
          "value": "2019-03-08T18:00:00.000+01:00",
          "grain": "hour"
        },
        "to": {
          "value": "2019-03-11T00:00:00.000+01:00",
          "grain": "hour"
        },
        "type": "interval"
      },
      "end": 44,
      "entity": "time",
      "confidence": 1.0
    }
  ],
  "text": "Je veux aller de toulouse à paris ce weekend"
}
```
Here we have trained our chatbot model to recognize, in this example, the intent "flight_search" and its entities ("time", "nb_passengers", "origin", "destination", "discover_category", "one_way", "round_trip", "flexibility")

## Training the model

In order to train our chatbot model to recognize the right itents and the right entities, we just have to launch the following line on a shell

```
$ python nlu_model.py
```
the nlu_model.py uses the "config_spacy.yml" file and a "train_data_res_final.json".
The "nlu_model.py" script contains 3 parts : first part is for training the model based on a data set (in this case "train_data_res_final.json"); the second is for running our model, testing it with some examples; the last one ask the user in the shell to tape a request, then returns a structured data like shown before. At the beginning, only the first part is uncommented, in order to train the model.

The "train_data_res_final.json" is - in our case - the data set in which is based the training; its format is as follow :

```
{
    "rasa_nlu_data": {
        "common_examples": [],
        "regex_features" : [],
        "lookup_tables"  : [],
        "entity_synonyms": []
    }
}
```
Regex features are a tool to help the classifier detect entities or intents and improve the performance.
Synonyms will map extracted entities to the same name, for example mapping “with my wife” to simply "romantic" (arguably).
The common_examples are used to train your model. You should put all of your training examples in the common_examples array. These examples are in the following format:

```
      {
        "entities": [
          {
            "end": 35,
            "entity": "origin",
            "start": 29,
            "value": "Ramsar"
          },
          {
            "end": 55,
            "entity": "destination",
            "start": 48,
            "value": "Guanaja"
          },
          {
            "end": 65,
            "entity": "nb_passengers",
            "start": 56,
            "value": "1"
          },
          {
            "end": 78,
            "entity": "round_trip",
            "start": 66,
            "value": "aller retour"
          }
        ],
        "intent": "flight_search",
        "text": "bonjour J'souhaite un vol de Ramsar destination Guanaja tout seul aller retour"
      },
```

As for the "config_spacy.yml"

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```
The common_examples are used to train your model. You should put all of your training examples in the common_examples array.
### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc

