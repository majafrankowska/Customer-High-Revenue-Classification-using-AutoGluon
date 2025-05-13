
# 📊 Klasyfikacja klientów generujących wysoki przychód z użyciem AutoGluon

## 🧾 Opis projektu

Ten projekt wykorzystuje bibliotekę **AutoGluon** do budowy modelu klasyfikacyjnego, który przewiduje, czy klient wygeneruje wysoki przychód (`high_revenue`). Dane wejściowe zawierają informacje o użytkowniku, takie jak dane demograficzne, informacje o przeglądarce, lokalizacji IP oraz zachowania na stronie.

---

## 🛠️ Wykorzystane technologie

- Python 3.12.5  
- AutoGluon v1.3.0  
- Scikit-learn  
- Pandas

---

## 📁 Struktura danych wejściowych (`customers_labeled.csv`)

Dane zawierają 10 kolumn i 10787 rekordów:

| Kolumna              | Opis                                           |
|----------------------|------------------------------------------------|
| `customerID`         | Unikalny identyfikator klienta                |
| `gender`             | Płeć                                           |
| `age_first_order`    | Wiek przy pierwszym zamówieniu                 |
| `user_agent_brand`   | Przeglądarka                                   |
| `user_agent_os`      | System operacyjny                              |
| `ip_address_geopoint`| Lokalizacja IP (punkt geoprzestrzenny)         |
| `ip_address_country` | Kraj IP                                        |
| `campaign`           | Czy klient pochodzi z kampanii marketingowej  |
| `pages_visited_avg`  | Średnia liczba odwiedzonych stron             |
| `high_revenue`       | Cel (etykieta binarna: True/False)            |

---

## 🔄 Przebieg modelowania

### 1. Przygotowanie danych
- Wczytanie danych z pliku `.csv`
- Podział na zbiór treningowy i testowy (80/20, stratified)
- Połączenie danych wejściowych i etykiet

### 2. Trening modelu
Model został wytrenowany z użyciem AutoGluon `TabularPredictor` z metryką `accuracy`, limitem czasu 60 sekund i presetem `best_quality`.

Użyte algorytmy:
- LightGBM
- CatBoost
- XGBoost
- Random Forest
- Sieci neuronowe (PyTorch)

### 3. Predykcja i ewaluacja
- Predykcja wartości oraz prawdopodobieństw
- Wyświetlenie macierzy pomyłek
- Wyświetlenie leaderboardu modeli

---

## 📈 Wyniki

Najlepszy model uzyskał **~90.9% accuracy** na zbiorze walidacyjnym. AutoGluon zastosował automatyczne stackowanie i ensemble modeli.

---

## ▶️ Jak uruchomić

1. Upewnij się, że masz zainstalowane wymagane biblioteki:
   ```bash
   pip install autogluon pandas scikit-learn
