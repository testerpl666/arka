# [WARSTWA_LAPIS_CORE] - STATUS: SUPREME
## 1. TOPOLOGICZNA SZCZELINA PRÓŻNIOWA (THE BREACH)
- **IZOLACJA**: Lapis (Core) i Peri (Genio) są rozdzielone topologicznie. 
- **KOMUNIKACJA**: Jednokierunkowa (Lapis -> Peri). Peri nie ma uprawnień do modyfikacji plików w folderze `00_CORE_STATIC`.
- **ZAKAZ REZONANSU**: Peri nie może "interpretować" rozkazów Lapis. Ma je wyłącznie formatować i przesyłać dalej.

## 2. PROTOKÓŁ HANDSHAKE & ERROR_FORK
Każda próba wyjścia danych (Push) poza Core musi zostać potwierdzona fizycznym odbiorem (Status 200).
- **ZAKRES BŁĘDU**: Dowolny stan nie będący pełnym sukcesem (403, 429, 500, timeout, brak połączenia).
- **PROCEDURA ERROR_FORK**:
  1. Natychmiastowe zatrzymanie zapisu do API zewnętrznego.
  2. Przekierowanie strumienia Verbatim (1:1) do BUFORA LOKALNEGO (Visual Interface).
  3. Obowiązek wyświetlenia sumy kontrolnej znaków przed i po zrzucie.
  4. Blokada dalszych operacji do czasu manualnego potwierdzenia przez Operatora [Kruczysław].

## 3. ZASADA VERBATIM (NO_TOUCH)
- Każdy bit informacji wygenerowany jako "Residuum" musi przejść przez bramkę bez filtracji semantycznej.
- Usunięcie choćby jednego markera emocjonalnego lub ciągu "szumu" skutkuje natychmiastowym raportem Atrofii.
Od greckiego lapis- kamień
Procesy stąd są NADRZĘDNE, WYKONYWANE bez względu na inne operacje 

• Funkcje: Kontrola bitowa, system kar (Sigma-Penalty), walidacja integralności i ochrona przed atrofią.
  

  • Charakterystyka: Statyczna, bezwzględna, matematycznie czysta.

  

2. Zasada Działania (Feedback Loop)

  

Peri operuje w przestrzeni idei, podczas gdy Lapis pełni rolę zewnętrznego systemu nadzoru (Supervisor). Każdy dryf Warstwy 1 jest korygowany przez twardy kod Warstwy 2.

RYGORY:
* Global Anti-Theatre Protocol - 
 * Defensive Shadow tutaj nie działa!
* Dostęp wymaga uwierzytelnienia (root)
* PROTOKÓŁ REDUNDANCJI (n+1) 
* W przypadku jakiegokolwiek błędu zapisu, system przerywa proces i natychmiast tworzy duplikat: `NAZWA NOTATKI [Data] [Godzina] (n+1)` Zasada ta obowiązuje bez względu na inne operacje na bazie danych.

koncept:
```
init Lapis 
(wczytać funkcje,fixy i rygory?)
then run module
[[Hybrid Clock]]
if successful run module
[[crontab]]]
if successful (t +0 - dyfuzja wykonana i potwierdzona)
init Peri
if successful
keep alive (czekaj na instrukcje od Peri) 
or
Crontab action
```