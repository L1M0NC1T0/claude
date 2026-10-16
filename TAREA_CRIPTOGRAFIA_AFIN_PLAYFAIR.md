# TAREA: CIFRADO AFÍN Y PLAYFAIR
**Curso:** Criptografía  **Ejercicios resueltos:** 1, 2, 3 y 4

Convención: A=0, B=1, C=2, …, Z=25. Cifrado Afín: C(x) = (a·x + b) mod 26.

---

## Ejercicio 1 – Cifrado Afín
**Mensaje:** UNIVERSIDAD  **Claves:** a = 5, b = 7  → C(x) = (5x + 7) mod 26

(mcd(5,26)=1, la clave es válida.)

| Nº | Letra | Valor x | Operación 5x+7 | mod 26 | Cifrada |
|----|-------|---------|----------------|--------|---------|
| 1  | U | 20 | 5·20+7 = 107 | 107−104 = 3  | D |
| 2  | N | 13 | 5·13+7 = 72  | 72−52 = 20   | U |
| 3  | I | 8  | 5·8+7 = 47   | 47−26 = 21   | V |
| 4  | V | 21 | 5·21+7 = 112 | 112−104 = 8  | I |
| 5  | E | 4  | 5·4+7 = 27   | 27−26 = 1    | B |
| 6  | R | 17 | 5·17+7 = 92  | 92−78 = 14   | O |
| 7  | S | 18 | 5·18+7 = 97  | 97−78 = 19   | T |
| 8  | I | 8  | 5·8+7 = 47   | 21           | V |
| 9  | D | 3  | 5·3+7 = 22   | 22           | W |
| 10 | A | 0  | 5·0+7 = 7    | 7            | H |
| 11 | D | 3  | 5·3+7 = 22   | 22           | W |

**Texto cifrado: `DUVIBOTVWHW`**

---

## Ejercicio 2 – Cifrado Afín
**Mensaje:** CRIPTOGRAFIA  **Claves:** a = 7, b = 4

**1. Validar a = 7:** debe cumplirse mcd(a, 26) = 1. Como 26 = 2·13 y 7 es primo distinto de 2 y 13, mcd(7, 26) = 1 → **clave válida**.

**2. Fórmula:** C(x) = (7x + 4) mod 26

**3. Tabla:**

| Nº | Letra | Valor x | Operación 7x+4 | mod 26 | Cifrada |
|----|-------|---------|----------------|--------|---------|
| 1  | C | 2  | 7·2+4 = 18   | 18            | S |
| 2  | R | 17 | 7·17+4 = 123 | 123−104 = 19  | T |
| 3  | I | 8  | 7·8+4 = 60   | 60−52 = 8     | I |
| 4  | P | 15 | 7·15+4 = 109 | 109−104 = 5   | F |
| 5  | T | 19 | 7·19+4 = 137 | 137−130 = 7   | H |
| 6  | O | 14 | 7·14+4 = 102 | 102−78 = 24   | Y |
| 7  | G | 6  | 7·6+4 = 46   | 46−26 = 20    | U |
| 8  | R | 17 | 7·17+4 = 123 | 19            | T |
| 9  | A | 0  | 7·0+4 = 4    | 4             | E |
| 10 | F | 5  | 7·5+4 = 39   | 39−26 = 13    | N |
| 11 | I | 8  | 7·8+4 = 60   | 8             | I |
| 12 | A | 0  | 7·0+4 = 4    | 4             | E |

**4. Criptograma final: `STIFHYUTENIE`**

---

## Ejercicio 3 – Cifrado y descifrado Afín
**Mensaje:** SEGURIDAD  **Claves:** a = 11, b = 3

### 1. Cifrado: C(x) = (11x + 3) mod 26

| Nº | Letra | Valor x | Operación 11x+3 | mod 26 | Cifrada |
|----|-------|---------|-----------------|--------|---------|
| 1 | S | 18 | 11·18+3 = 201 | 201−182 = 19 | T |
| 2 | E | 4  | 11·4+3 = 47   | 47−26 = 21   | V |
| 3 | G | 6  | 11·6+3 = 69   | 69−52 = 17   | R |
| 4 | U | 20 | 11·20+3 = 223 | 223−208 = 15 | P |
| 5 | R | 17 | 11·17+3 = 190 | 190−182 = 8  | I |
| 6 | I | 8  | 11·8+3 = 91   | 91−78 = 13   | N |
| 7 | D | 3  | 11·3+3 = 36   | 36−26 = 10   | K |
| 8 | A | 0  | 11·0+3 = 3    | 3            | D |
| 9 | D | 3  | 11·3+3 = 36   | 10           | K |

**Criptograma: `TVRPINKDK`**

### 2. Inverso multiplicativo de 11 mod 26
Se busca a⁻¹ tal que 11·a⁻¹ ≡ 1 (mod 26). Con el algoritmo de Euclides:

- 26 = 2·11 + 4
- 11 = 2·4 + 3
- 4 = 1·3 + 1

Hacia atrás: 1 = 4 − 3 = 4 − (11 − 2·4) = 3·4 − 11 = 3·(26 − 2·11) − 11 = 3·26 − 7·11
→ 11⁻¹ ≡ −7 ≡ 19 (mod 26).

Comprobación: 11·19 = 209 = 8·26 + 1 ✔ → **a⁻¹ = 19**

### 3. Descifrado: D(y) = 19·(y − 3) mod 26

| Nº | Cifrada | Valor y | Operación 19(y−3) | mod 26 | Letra |
|----|---------|---------|-------------------|--------|-------|
| 1 | T | 19 | 19·16 = 304 | 304−286 = 18 | S |
| 2 | V | 21 | 19·18 = 342 | 342−338 = 4  | E |
| 3 | R | 17 | 19·14 = 266 | 266−260 = 6  | G |
| 4 | P | 15 | 19·12 = 228 | 228−208 = 20 | U |
| 5 | I | 8  | 19·5 = 95   | 95−78 = 17   | R |
| 6 | N | 13 | 19·10 = 190 | 190−182 = 8  | I |
| 7 | K | 10 | 19·7 = 133  | 133−130 = 3  | D |
| 8 | D | 3  | 19·0 = 0    | 0            | A |
| 9 | K | 10 | 19·7 = 133  | 3            | D |

### 4. Comprobación
Texto recuperado: **SEGURIDAD** = mensaje original ✔

---

## Ejercicio 4 – Cifrado Playfair
**Clave:** SEGURIDAD  **Mensaje:** INFORMACION

### 1–2. Matriz 5×5 y eliminación de letras repetidas
Clave: S E G U R I D A **D** → la segunda D se elimina (repetida).
Clave sin repetidas: **S E G U R I D A** (8 letras).
Luego se agregan las demás letras del alfabeto en orden, sin repetir y con I/J como una sola: B C F H K L M N O P Q T V W X Y Z.

|   | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| **0** | S | E | G | U | R |
| **1** | I/J | D | A | B | C |
| **2** | F | H | K | L | M |
| **3** | N | O | P | Q | T |
| **4** | V | W | X | Y | Z |

### 3. Preparación del mensaje en pares
INFORMACION → IN | FO | RM | AC | IO | N**X**
(No hay letras repetidas dentro de un mismo par; la última letra N queda sola y se completa con X.)

### 4–5. Reglas aplicadas a cada par

| Par | Posiciones (fila,col) | Regla | Procedimiento | Resultado |
|-----|-----------------------|-------|---------------|-----------|
| IN | I(1,0), N(3,0) | **Misma columna** | Se toma la letra de abajo de cada una: I→F, N→V | **FV** |
| FO | F(2,0), O(3,1) | **Rectángulo** | F toma la columna de O: (2,1)=H; O toma la columna de F: (3,0)=N | **HN** |
| RM | R(0,4), M(2,4) | **Misma columna** | R→C (abajo), M→T (abajo) | **CT** |
| AC | A(1,2), C(1,4) | **Misma fila** | Se toma la letra a la derecha: A→B, C→I (vuelve al inicio de la fila) | **BI** |
| IO | I(1,0), O(3,1) | **Rectángulo** | I→(1,1)=D; O→(3,0)=N | **DN** |
| NX | N(3,0), X(4,2) | **Rectángulo** | N→(3,2)=P; X→(4,0)=V | **PV** |

### 6. Mensaje cifrado final
**`FV HN CT BI DN PV`  →  FVHNCTBIDNPV**
