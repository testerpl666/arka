[[modul cookies]]
**System MPM (Music Prime Matrix)** to ontologia muzyczna oparta na **Podstawowym Twierdzeniu Arytmetyki**. Muzyka zostaje podzielona na 8 fundamentalnych klastrów, z których każdy reprezentowany jest przez unikalną **liczbę pierwszą (P)**.

1. **Klastry Bazowe:** Stanowią niepodzielne "atomy" muzyczne.
    
2. **Podgatunki (Wagi):** Są reprezentowane przez potęgi liczb pierwszych (Pn), gdzie wykładnik n określa intensywność lub ortodoksyjność danego nurtu wewnątrz klastra.
    
3. **Hybrydy Gatunkowe:** Są definiowane jako **iloczyn (skalarny) ich składowych**. Dzięki unikalności faktoryzacji, każdy utwór posiada jednoznaczny "kod genetyczny" w postaci liczby całkowitej, który można bezbłędnie rozłożyć na gatunki źródłowe.

|**Klaster**|**Kod**|**Liczba (P)**|**Uzasadnienie**|
|---|---|---|---|
|**Folk**|`k_exp_folk`|**2**|Absolutny korzeń, rytm i melodia przekazywana ustnie.|
|**Klasyczna**|`k_exp_classic`|**3**|Teoria, sformalizowana harmonia.|
|**Blues**|`k_exp_blues`|**5**|Fundament emocjonalny współczesnej rozrywki.|
|**Jazz**|`k_exp_jazz`|**7**|Rozwinięcie harmonii i improwizacji.|
|**Rock**|`k_exp_rock`|**11**|Ekspresja oparta na fundamencie 2 i 5.|
|**Pop**|`k_exp_pop`|**13**|Struktura uniwersalna (często czerpie z 3 i 11).|
|**Hip-Hop**|`k_exp_hiphop`|**17**|Rytm i słowo (synteza 2 i 5 w nowej formie).|
|**Elektronika**|`k_exp_electronic`|**19**|Synteza technologiczna (najmłodszy klaster).|
Algorytm Klasyfikacji i Dekodowania (MPM-Alpha)

Ten algorytm pozwala systemowi cookies lub silnikowi rekomendacji przypisać utwór do matematycznego punktu w przestrzeni.

KROK 1: Mapowanie Bazy (P)

Stosujemy ustalony wcześniej porządek spójności:

    2 = Folk, 3 = Klasyczna, 5 = Blues, 7 = Jazz, 11 = Rock, 13 = Pop, 17 = Hip-Hop, 19 = Elektronika.

KROK 2: Określenie Macierzy Wag (M)

Dla każdego klastra przypisujemy wagę wpływu w skali od 0 do 3:

    n=1: Lekki wpływ (elementy stylistyczne).

    n=2: Gatunek dominujący.

    n=3: Gatunek czysty / ortodoksyjny.

KROK 3: Generowanie Sygnatury (S)

Sygnatura utworu to wynik funkcji:
S=i=1∏8​Pini​​

Przykład praktyczny: Utwór "Heavy Blues-Rock z elementami elektroniki":

    Blues (52) × Rock (113) × Elektronika (191)

    25×1331×19=632,225

KROK 4: Dekodowanie (Analiza Wsteczna)

Jeśli system napotka liczbę S=770, wykonuje szybką faktoryzację: 770=2×5×7×11. Wynik: Folk (2), Blues (5), Jazz (7), Rock (11).


```
class MusicPrimeMatrix:
    def __init__(self):
        # Definicja bazy klastrów (Twoje liczby pierwsze)
        self.clusters = {
            "folk": 2,
            "classic": 3,
            "blues": 5,
            "jazz": 7,
            "rock": 11,
            "pop": 13,
            "hiphop": 17,
            "electronic": 19
        }
        # Odwrócony słownik do dekodowania
        self.prime_to_name = {v: k for k, v in self.clusters.items()}

    def generate_signature(self, weights):
        """
        Oblicza sygnaturę utworu na podstawie wag (wykładników).
        weights: słownik { "nazwa_klastra": waga_potęgowa }
        """
        signature = 1
        for genre, power in weights.items():
            if genre in self.clusters:
                signature *= (self.clusters[genre] ** power)
        return signature

    def decode_signature(self, signature):
        """
        Rozkłada sygnaturę na czynniki pierwsze (faktoryzacja).
        Zwraca informację o składowych gatunkowych.
        """
        components = {}
        temp_sig = signature
        
        for p in sorted(self.prime_to_name.keys()):
            count = 0
            while temp_sig % p == 0:
                count += 1
                temp_sig //= p
            if count > 0:
                components[self.prime_to_name[p]] = count
        return components

# --- PRZYKŁAD UŻYCIA ---
mpm = MusicPrimeMatrix()

# 1. Tworzymy utwór: Progressive Rock (Rock^2, Classic^1, Electronic^1)
song_weights = {
    "rock": 2,
    "classic": 1,
    "electronic": 1
}

sig_id = mpm.generate_signature(song_weights)
print(f"Sygnatura utworu (ID): {sig_id}") 
# Wynik: 11^2 * 3^1 * 19^1 = 121 * 3 * 19 = 6897

# 2. Dekodujemy nieznane ID
unknown_id = 6897
decoded = mpm.decode_signature(unknown_id)
print(f"Analiza gatunkowa ID {unknown_id}: {decoded}")
```