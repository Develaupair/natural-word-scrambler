from sys import argv
from random import shuffle
import pyperclip as pc

CLIPBOARDMODE = False
ALPHABET = "abcdefghijklmnopqrstuvwxyz"

text = "".join([x for x in argv[1:]]).strip()
if text == "":
    CLIPBOARDMODE = True
    print("<using clipboard mode>")
    text = pc.paste().strip()
    if text == "":
        print("<no text found in clipboard or as parameter!>")

def shuffled(list):
    l = list
    shuffle(l)
    return(l)

def scrambleword(word):
    if len(word) < 4:
        return word
    original = word
    while word == original:
        word = original[1:-1]
        atleast2characters = len(word.replace(word[0], "")) > 0
        if not atleast2characters:
            return original
        word = original[0] + "".join(shuffled(list(word))) + original[-1]
    return(word)


ALPHABET = ALPHABET.lower() + ALPHABET.upper()
ALIST = [x for x in ALPHABET]
map = []
words = []
nextword = ""

for character in text:
    if character in ALIST:
        nextword = nextword + character
    else:
        words.append(nextword)
        nextword = ""
        map.append("")
        map.append(character)
words.append(nextword)
map.append("")

output = ""
for item in map:
    if item == "":
        output = output + str(scrambleword(words[0]))
        words = words[1:]
    else:
        output = output + item

if CLIPBOARDMODE:
    pc.copy(output)
    print("<text in clipboard replaced!>")
else:
    print("\n\n" + output)
   
