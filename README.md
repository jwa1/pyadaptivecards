# PyAdaptiveCards

*Author adaptive cards in pure python*

[![PyPi](https://img.shields.io/pypi/v/pyadaptivecards.svg)](https://pypi.python.org/pypi/pyadaptivecards)
[![Travis](https://img.shields.io/travis/sQu4rks/pyadaptivecards.svg)](https://travis-ci.org/sQu4rks/pyadaptivecards)
[![ReadTheDocs](https://readthedocs.org/projects/pyadaptivecards/badge/?version=latest)](https://pyadaptivecards.readthedocs.io/en/latest/?badge=latest)
[![PyUp](https://pyup.io/repos/github/sQu4rks/pyadaptivecards/shield.svg)](https://pyup.io/repos/github/sQu4rks/pyadaptivecards/)


---

## Introduction 

[Adaptive Cards](https://adaptivecards.io/) are a great way to extend your bots interactions. However, writing the JSON required to specify the card layout by hand can be cumbersome and error prone. And while using a [designer](https://adaptivecards.io/designer/) is a good way to manually create cards this does not cover cards that are generated by code. PyAdaptiveCards allows you to author cards in native python without ever touching the underlying json. 

A code sample says more then a thousand words so the following code snippet ...

```python
from pyadaptivecards.card import AdaptiveCard
from pyadaptivecards.inputs import Text, Number
from pyadaptivecards.components import TextBlock
from pyadaptivecards.actions import Submit

greeting = TextBlock("Hey hello there! I am a adaptive card")
first_name = Text('first_name', placeholder="First Name")
age = Number('age', placeholder="Age")

submit = Submit(title="Send me!")

card = AdaptiveCard(body=[greeting, first_name, age], actions=[submit])
card_json = card.to_json(pretty=True)
print(card_json)
```

... produces this json ...

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "actions": [
        {
            "title": "Send me!",
            "type": "Action.Submit"
        }
    ],
    "body": [
        {
            "text": "Hey hello there! I am a adaptive card",
            "type": "TextBlock"
        },
        {
            "id": "first_name",
            "placeholder": "First name",
            "type": "Input.Text"
        },
        {
            "id": "age",
            "placeholder": "Age",
            "type": "Input.Number"
        }
    ],
    "type": "AdaptiveCard",
    "version": "1.1"
}
```

... which looks like this in [Webex Teams](https://teams.webex.com) ...

![screenshot of card in webex teams](cards_sample.png)

## Features

- Supports all components, options and features of adaptive cards version 1.1
- Create adaptive cards from pure python

## Installation

You can install PyAdaptiveCards using pip by issuing

```bash
$ pip install pyadaptivecards
```

For more information on how to use this package please check the project documentation at https://pyadaptivecards.readthedocs.io.

## Authors & Maintainers

- Marcel Neidinger <mneiding@cisco.com>

## Credits

The following resources were influential in the creation of this project:

- This package was created with [Cookiecutter](https://github.com/audreyr/cookiecutter) and a derivative of the[audreyr/cookiecutter-pypackage](https://github.com/audreyr/cookiecutter-pypackage) project template.

## License

This project is licensed to you under the terms of the [Cisco SampleCode License](./LICENSE).
