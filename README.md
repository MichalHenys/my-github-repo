from collections import Counter

"""
projekt_1.py: první projekt do Engeto Online Python Akademie
author: Michal Henyš
email: henysmichal87@gmail.com
discord: Michal Henys
"""

TEXT = ['''
Situated about 10 miles west of Kemmerer,
Fossil Butte is a ruggedly impressive
topographic feature that rises sharply
some 1000 feet above Twin Creek Valley
to an elevation of more than 7500 feet
above sea level. The butte is located just
north of US 30N and the Union Pacific Railroad,
which traverse the valley. ''',
'''At the base of Fossil Butte are the bright
red, purple, yellow and gray beds of the Wasatch
Formation. Eroded portions of these horizontal
beds slope gradually upward from the valley floor
and steepen abruptly. Overlying them and extending
to the top of the butte are the much steeper
buff-to-white beds of the Green River Formation,
which are about 300 feet thick.''',
'''The monument contains 8198 acres and protects
a portion of the largest deposit of freshwater fish
fossils in the world. The richest fossil fish deposits
are found in multiple limestone layers, which lie some
100 feet below the top of the butte. The fossils
represent several varieties of perch, as well as
other freshwater genera and herring similar to those
in modern oceans. Other fish such as paddlefish,
garpike and stingray are also present.'''
]

# vyžádání uživatelsého jména
user = input("username: ").strip()

# vyžádání hesla
password = input("password: ").strip()

# registrovaní uživatelé pro kontrolu
registred_users = {
  "bob" : "123",
  "ann" : "pass123",
  "mike" : "password123",
  "liz" : "pass123"  
}

# dotaz zda jsou uživatelé registovaní
if (user, password) in registred_users.items():
  print(40 * "-")
  print(f"Welcome to the app, {user}")
  print("We have 3 texts to be analyzed.")
  print(40 * "-")

  # pustit cyklus na analýzu textu
  # program se zeptá na číslo od 1 - 3, pokud není číslo nebo je vyšší, ukončí se
  while choice := input("Enter a number btw. 1 and 3 to select: "):
    print("-" * 40)
    if choice in ["1", "2", "3"]:
      # vypíše počet slov
      # rozdělení textu na seznam
      index = int(choice) - 1
      selected_text = TEXT[index]

      words = selected_text.split()    
      print(f"There are {len(words)} words in the selected text.")

      big_first = [big_w for big_w in words if big_w[0].isupper()]
      print(f"There are {len(big_first)} titlecase words.")

      # určení, zda je celé slovo psané jen velkými písmeny
      words_upper = [upper_w for upper_w in words if upper_w.isupper() and upper_w.isalpha()]
      print(f"There are {len(words_upper)} uppercase words.")

      # určení, zda je celé slovo psané jen malými písmeny včetně lov s čísly
      words_lower = [lower_w for lower_w in words if lower_w.islower()]
      print(f"There are {len(words_lower)} lowercase words.")

      # kolik je numerických částí ve stringu a jejich součet
      words_numeric = [int(num_w) for num_w in words if num_w.isnumeric()]
      sum_numeric = sum(words_numeric)             
      print(f"There are {len(words_numeric)} numeric strings.")
      print(f"The sum of all the numbers {sum_numeric}")

      # Tvorba tabulky a přidání hodnot, naiportování Counteru
      word_lengths = [len(word.strip(",.")) for word in words]

      # Spočítání četnosti každé délky slova
      length_counts = Counter(word_lengths)

      # Seřazení délek slov podle jejich délky (od nejmenší po největší)
      sorted_lengths = sorted(length_counts.items())
      
      # Maximální šířka grafu
      max_bar_width= max(length_counts.values())
      

      # Výpis hlavičky
      print("-" * 40)
      print(f'{"LEN":>2}|{"OCCURRENCES".center(max_bar_width + 2)}|{"NR.":>2}')
      print("-" * 40)

      # Škálování délky hvězdičkového grafu
      for row_length, col_count in sorted_lengths:
          scaled_count = col_count
          bar = '*' * scaled_count
          print(f'{row_length:3}|{bar:<{max_bar_width + 2}}|{col_count}')


    elif not choice.isdigit():
      print("This is not a number.")
    else:
      print("You entered an incorrect selection number.")
    break

else:
  print("Unregistered user, terminating the program..")