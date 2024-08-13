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

# rehistrovaní uživatelé pro kontrolu
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
    if choice == "1":
      # vypíše počet slov
      # rozdělení textu na seznam
      words = TEXT[0].split()
      words_list = []
      for w in words:
        words_list.append(w)     
      print(f"There are {len(words)} words in the selected text.")

      big_first = []
      for i in words:
        if i[0].isupper(): # určení, zda slovo začíná velkým písmenem na pozici [0]
          big_first.append(i)
      print(f"There are {len(big_first)} titlecase words.")

      # určení, zda je celé slovo psané jen velkými písmeny
      words_upper = []
      for b in words:
        if b.isupper() and b.isalpha():
          words_upper.append(b)
      print(f"There are {len(words_upper)} uppercase words.")

      # určení, zda je celé slovo psané jen malými písmeny včetně lov s čísly
      words_lower = []
      for b in words:
        if b.islower():
          words_lower.append(b)
      print(f"There are {len(words_lower)} lowercase words.")

      # kolik je numerických částí ve stringu a jejich součet
      words_numeric = []
      sum_numeric = 0      
      for n in words:
        if n.isnumeric():
          #přičtení hodoty každého stringu převedeného na int do words_numeric
          sum_numeric += int(n)
          words_numeric.append(n)
      print(f"There are {len(words_numeric)} numeric strings.")
      print(f"The sum of all the numbers {sum_numeric}")

      # Tvorba tabulky a přidání hodnot, naiportování Counteru
      word_lengths = [len(word.strip(",.")) for word in words]

      # Spočítání četnosti každé délky slova
      length_counts = Counter(word_lengths)

      # Seřazení délek slov podle jejich délky (od nejmenší po největší)
      sorted_lengths = sorted(length_counts.items())

      # Maximální šířka grafu
      max_bar_width = 18

      # Výpis hlavičky
      print("-" * 40)
      print(f'{"LEN":>2}|{"OCCURRENCES".center(max_bar_width)}|{"NR.":>2}')
      print("-" * 40)

      for length, count in sorted_lengths:
          # Škálování délky hvězdičkového grafu
          scaled_count = count
          bar = '*' * scaled_count
          print(f'{length:3}|{bar:<{max_bar_width}}|{count}')
      

    # Výběr 2. možnosti
    elif choice == "2":
      # vypíše počet slov
      # rozdělení textu na seznam
      words = TEXT[1].split()
      words_list = []
      for w in words:
        words_list.append(w)     
      print(f"There are {len(words)} words in the selected text.")

      big_first = []
      for i in words:
        if i[0].isupper(): # určení, zda slovo začíná velkým písmenem na pozici [0]
          big_first.append(i)
      print(f"There are {len(big_first)} titlecase words.")

      # určení, zda je celé slovo psané jen velkými písmeny
      words_upper = []
      for b in words:
        if b.isupper() and b.isalpha():
          words_upper.append(b)
      print(f"There are {len(words_upper)} uppercase words.")

      # určení, zda je celé slovo psané jen malými písmeny včetně lov s čísly
      words_lower = []
      for b in words:
        if b.islower():
          words_lower.append(b)
      print(f"There are {len(words_lower)} lowercase words.")

      # kolik je numerických částí ve stringu a jejich součet
      words_numeric = []
      sum_numeric = 0      
      for n in words:
        if n.isnumeric():
          #přičtení hodoty každého stringu převedeného na int do words_numeric
          sum_numeric += int(n)
          words_numeric.append(n)
      print(f"There are {len(words_numeric)} numeric strings.")
      print(f"The sum of all the numbers {sum_numeric}")

      # Tvorba tabulky a přidání hodnot, naiportování Counteru
      word_lengths = [len(word.strip(",.")) for word in words]
  
      # Spočítání četnosti každé délky slova
      length_counts = Counter(word_lengths)
  
      # Seřazení délek slov podle jejich délky (od nejmenší po největší)
      sorted_lengths = sorted(length_counts.items())
      
  
      # Maximální šířka grafu
      max_bar_width = 18
  
      # Výpis hlavičky
      print("-" * 40)
      print(f'{"LEN":>2}|{"OCCURRENCES".center(max_bar_width)}|{"NR.":>2}')
      print("-" * 40)
  

      for length, count in sorted_lengths:
          # Škálování délky hvězdičkového grafu
          scaled_count = count
          bar = '*' * scaled_count
          print(f'{length:3}|{bar:<{max_bar_width}}|{count}')
      

    # Výběr 3. možnosti
    elif choice == "3":
      # vypíše počet slov
      # rozdělení textu na seznam
      words = TEXT[2].split()
      words_list = []
      for w in words:
        words_list.append(w)     
      print(f"There are {len(words)} words in the selected text.")

      big_first = []
      for i in words:
        if i[0].isupper(): # určení, zda slovo začíná velkým písmenem na pozici [0]
          big_first.append(i)
      print(f"There are {len(big_first)} titlecase words.")

      # určení, zda je celé slovo psané jen velkými písmeny
      words_upper = []
      for b in words:
        if b.isupper() and b.isalpha():
          words_upper.append(b)
      print(f"There are {len(words_upper)} uppercase words.")

      # určení, zda je celé slovo psané jen malými písmeny včetně lov s čísly
      words_lower = []
      for b in words:
        if b.islower():
          words_lower.append(b)
      print(f"There are {len(words_lower)} lowercase words.")

      # kolik je numerických částí ve stringu a jejich součet
      words_numeric = []
      sum_numeric = 0      
      for n in words:
        if n.isnumeric():
          #přičtení hodoty každého stringu převedeného na int do words_numeric
          sum_numeric += int(n)
          words_numeric.append(n)
      print(f"There are {len(words_numeric)} numeric strings.")
      print(f"The sum of all the numbers {sum_numeric}")

      # Tvorba tabulky a přidání hodnot, naiportování Counteru
      word_lengths = [len(word.strip(",.")) for word in words]

      # Spočítání četnosti každé délky slova
      length_counts = Counter(word_lengths)

      # Seřazení délek slov podle jejich délky (od nejmenší po největší)
      sorted_lengths = sorted(length_counts.items())
     
      # Maximální šířka grafu
      max_bar_width = 18

      # Výpis hlavičky
      print("-" * 40)
      print(f'{"LEN":>2}|{"OCCURRENCES".center(max_bar_width)}|{"NR.":>2}')
      print("-" * 40)


      for length, count in sorted_lengths:
          # Škálování délky hvězdičkového grafu
          scaled_count = count
          bar = '*' * scaled_count
          print(f'{length:3}|{bar:<{max_bar_width}}|{count}')
      

    elif not int(choice.isdigit()):
      print("This is not a number.")
    else:
      print("You entered an incorrect selection number.")
    break

else:
  print("unregistered user, terminating the program..")





