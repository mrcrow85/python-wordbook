# Python wordbook app

This app has two functions: a dictionary and a text translator.

- For the dictionary, it uses [wordnet](https://www.nltk.org/howto/wordnet.html) in order to find definitions to English words provided by the user. Similar to [this](http://wordnetweb.princeton.edu/perl/webwn).

- For the translation, it uses [`googletrans`](https://pypi.org/project/googletrans/) which implements the Google Translate API.

## Why?
Nothing in particular, playing a bit with Python as part of my self-training.

## Requirements
- Python 3.8
- [Pipenv](https://pypi.org/project/pipenv/)

## Instructions
1. Install the dependencies and the [wordnet data](https://www.nltk.org/data.html):

    ```bash
    make install
    ```

1. Execute the app:

    ```bash
    make run
    ```

### Dictionary
To use the dictionary functionality you can do it in 2 ways:

- Executing the main app:

    ```bash
    $ make run
    Select the option you like to run:
                1) Find definitions
                2) Translate
    ```
    On the prompt, type 1 to select the first option, then enter an English word. It will display a list of definitions:
    ```
    1
    Enter an English word:
    dog
    1. A member of the genus canis (probably descended from the common wolf) that has been domesticated by man since prehistoric times; occurs in many breeds.
    2. A dull unattractive unpleasant girl or woman.
    3. Informal term for a man.
    4. Someone who is morally reprehensible.
    5. A smooth-textured sausage of minced beef or pork usually smoked; often served on a bread roll.
    6. A hinged catch that fits into a notch of a ratchet to move a wheel forward or prevent it from moving backward.
    7. Metal supports for logs in a fireplace.
    8. Go after with the intent to catch.
    ```

- Executing the dictionary app:
    ```
    pipenv run python wordbook/dictionary.py
    ```
    You can also pass a word directly to get the results:
    ```
    pipenv run python wordbook/dictionary.py dog
    ```

### Translation
To use the translation functionality you can do it in 3 ways, the same as the dictionary, but with an additional file input:

- Executing the main app:

    ```bash
    $ make run
    Select the option you like to run:
                1) Find definitions
                2) Translate
    ```
    On the prompt, type 2 to select the second option. Then you need to provide a source language, a destination language and the text to translate:
    
    (**NOTE:** This uses the Google Translate api, so you can supply any language supported by it.)
    ```
    2
    Enter the source language: en
    Enter the destination language: es
    Enter a text to translate: This is awesome!
    ??Esto es asombroso!
    ```

- Executing the translate app:
    ```
    pipenv run python wordbook/translate.py
    ```
    You can also pass an English text to automatically translate it to Spanish (be careful with special characters, you might need to escape them):
    ```
    $ pipenv run python wordbook/translate.py "This is awesome\!"
    ??Esto es asombroso!
    ```
    It's possible to override the source and destination languages with `--from` and `--to` flags respectively:
    ```
    $ pipenv run python wordbook/translate.py "Hola, como estas?" --from es --to de
    Hallo, wie geht es dir?
    ```

- Translating a file:

    You can use the `-f` or `--file` flag on the translate app to translate the contents of a `.txt` file. It will generate a translated file in `data/output.txt`
    ```
    pipenv run python wordbook/translate.py -f path/to/file.txt --from es --to de
    ```

## Tests
You can run the unit tests with:
```
make test
```
You can also format and lint the code with:
```
make lint
```
