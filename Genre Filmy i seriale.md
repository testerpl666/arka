[[modul cookies]]
**System CPM (Cinema Prime Matrix)** to ontologia dla filmów i seriali oparta na **Podstawowym Twierdzeniu Arytmetyki**. Film / serial zostaje podzielony na 8 fundamentalnych klastrów, z których każdy reprezentowany jest przez unikalną **liczbę pierwszą (P)**.

| **Klaster**              | **Kod**             | **Liczba (P)** | **Charakterystyka**                                |
| ------------------------ | ------------------- | -------------- | -------------------------------------------------- |
| **Dramat**               | `v_exp_drama`       | **2**          | Ludzkie emocje, relacje, fundament narracji.       |
| **Komedia**              | `v_exp_comedy`      | **3**          | Humor, satyra, lekkość formy.                      |
| **Akcja / Przygoda**     | `v_exp_action`      | **5**          | Dynamika, tempo, fizyczność.                       |
| **Sci-Fi / Fantasy**     | `v_exp_speculative` | **7**          | Wyobraźnia, światotwórstwo, technologia.           |
| **Horror**               | `v_exp_horror`      | **11**         | Strach, napięcie, pierwotne instynkty.             |
| **Kryminał / Thriller**  | `v_exp_crime`       | **13**         | Zagadka, suspens, mroczna strona społeczeństwa.    |
| **Dokument / Biografia** | `v_exp_doc`         | **17**         | Prawda, fakty, edukacja.                           |
| **Musical / Animacja**   | `v_exp_artistic`    | **19**         | Stylizacja, forma wizualna/muzyczna ponad realizm. |
### Algorytm Sygnatury Filmowej (Sv​)

Podobnie jak w muzyce, stosujemy wagi (potęgi n=1,2,3), aby określić dominację gatunku.

Sv​=i=1∏8​Pini​​
#### Przykłady Hybryd Filmowych:

- **"Incepcja" (Sci-Fi + Akcja + Thriller):**
    
    - 72 (Sci-Fi) × 52 (Akcja) × 131 (Thriller) = 49×25×13=15,925
        
- **"Parasite" (Dramat + Komedia + Thriller):**
    
    - 22 (Dramat) × 31 (Komedia) × 132 (Thriller) = 4×3×169=2,028
        
- **"Mad Max: Na drodze gniewu" (Akcja + Sci-Fi):**
    
    - 53 (Ekstremalna Akcja) × 71 (Sci-Fi/Dystopia) = 125×7=875

```
class MoviePrimeMatrix:
    def __init__(self):
        self.clusters = {
            "drama": 2,
            "comedy": 3,
            "action": 5,
            "scifi": 7,
            "horror": 11,
            "crime": 13,
            "documentary": 17,
            "animation": 19
        }

    def get_movie_id(self, weights):
        signature = 1
        for genre, power in weights.items():
            signature *= (self.clusters.get(genre, 1) ** power)
        return signature

# Przykład: Film "Alien" (Obcy)
# Horror (11) do potęgi 2, Sci-Fi (7) do potęgi 2
alien_id = MoviePrimeMatrix().get_movie_id({"horror": 2, "scifi": 2})
print(f"ID filmu Obcy: {alien_id}") # Wynik: 5929
```