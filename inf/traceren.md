# Traceren en herschrijven van programma's

**Tim Steenvoorden (Open Universiteit)**

Leren programmeren is niet alleen het kunnen schrijven van code, en ook niet
alleen het kunnen lezen van code. Uiteindelijk moet een programmeur een
duidelijk beeld hebben van wat een computer doet, op het moment dat code wordt
uitgevoerd. Hiertoe dient een “notional machine”: een denkbeeldige machine in
je hoofd waarmee je een programma stap-voor-stap kunt uitvoeren. Voor
imperatieve talen kun je gebruik maken van traceertabellen, voor functionele
talen van herschrijven. In deze workshop introduceer ik beide methoden en geef
aan hoe je ze kunt gebruiken voor leerlingen om code te begrijpen.

**Tim Steenvoorden** is universitair docent aan de Open Universiteit en geeft daar
vakken over functioneel programmeren, concepten van programmeertalen, en
besturingssystemen. Bij Inf4All geeft hij het vak alternatieve
programmeermodellen. Zijn onderzoeksinteresses liggen in het ontwerpen,
implementeren en verifiëren van programmeertalen. Daarnaast heeft hij de
afgelopen jaren bijgedragen aan de lesmodules algoritmiek en cognitive
computing voor het nieuwe informatica curriculum.

De programmacode bij deze sessie:

```Python
def section(name):
  print()
  print("====", name, "example", "====")


section("Product")

"https://pastefy.app/kflGA7c2"
inventory = [
  {"name": "piano",  "quantity": 2,   "price": 5000},
  {"name": "tv",     "quantity": 20,  "price": 1000},
  {"name": "teddy",  "quantity": 54,  "price": 25},
  {"name": "pencil", "quantity": 120, "price": 1},
]

print(inventory[2])


section("Total")

def stock_total(products):
  som = 0
  i = 0
  while i < len(products):
    som += products[i]["quantity"]
    i += 1
  return som

def price_total(products):
  som = 0
  i = 0
  while i < len(products):
    som += products[i]["price"]
    i += 1
  return som

def price_total_rec(products):
  match products:
    case []:
      return 0
    case first, *rest:
      return first["price"] + price_total_rec(rest)

print(stock_total(inventory))
print(price_total(inventory))
print(price_total_rec(inventory))


section("Average")

def average_price(products):
  return price_total(products) / len(products)

print(average_price(inventory))


section("Palindrome")

def palindrome(chars):
  match chars:
    case [] | [_]:
      return True
    case first, *middle, last:
      return first == last and palindrome(middle)

print(palindrome(list("")))
print(palindrome(list("a")))
print(palindrome(list("rar")))
print(palindrome(list("raar")))
print(palindrome(list("lepel")))
print(palindrome(list("not")))
print(palindrome(list("expensive")))
```