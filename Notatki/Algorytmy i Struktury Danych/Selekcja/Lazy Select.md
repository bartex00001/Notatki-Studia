**Dane:**
Ciąg elementów $T[1\dots n]$ z porządkiem liniowym.

> Zakładamy bez straty ogólności, że liczby są różne.

**Zadanie:**
Znaleźć $k$-tą liczbę w kolejności według danego porządku.

Będziemy chcieli z ciągu elementów $T$ wybrać losową próbkę $R$ na tyle małą, by potrafić ją posortować dosyć szybko.
Na podstawie tych elementów chcemy wybrać wartości $L,H$ takie, że z dużym prawdopodobieństwem szukany $k$-ty element ma wartość pomiędzy $L,H$. Dalej sortujemy wszystkie elementy o wartościach pomiędzy $L,H$, by następnie *po prostu* wybrać $k$-ty element.

Algorytm realizują następujące kroki:

1. Wybierz losowo, *z powtórzeniami* próbkę $R$ złożoną z $n^{3/4}$ elementów.
2. Posortuj $R$ w czasie $O(n^{3/4}\log n)$
3. $x \leftarrow kn^{-1/4}$; $L \leftarrow R[l]$; $H \leftarrow R[h]$;
4. Policz $r_{s}(L) = \text{ile elementów jest mniejszych niż L}$
   Policz $P = \{y \in S \mid L \le y \le H\}$
5. Sprawdź, czy 
	1. $k$-ty element znajduje się w $P$ – czy $r_{s}(L) < k \le |P| + r_{s}(L)$
	2. Czy zbiór $P$ jest odpowiednio mały: $|P| \le 4n^{3/4} + 2$
	3. Jeśli `5.1` lub `5.2` nie zachodzi, to wróć do `1`
6. Posortuj $P$, a następnie wybierz oczekiwany element.

### Złożoność Obliczeniowa

**Lemat:**
Z prawdopodobieństwem $1 - O\left( n^{-1/4} \right)$ algorytm potrzebuje tylko jednej iteracji.

**d-d:**
1. Pokazujemy, że $kn^{-1/4}$ jest wartością oczekiwaną liczby elementów mniejszych niż $k$-ty w $R$
2. Pokazujemy, że wariancja tej zmiennej losowej jest mniejsza niż $\sqrt{ n }$
3. Korzystamy z [[Nierówność Czebyszewa|nierówności Czebyszewa]]

#TODO  Uzupełnić dowód na podstawie *R.Motwani, P.Raghavan, Randomized Algorithms*.

> Dowód tego lematu ponoć wykracza poza zakres wykładu.
