# Biseccion
# -*- coding: utf-8 -*-
"""
@author: Roberto Drp
         César Otero
         Ariadna Gallegos
"""
#Método de bisección
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

def f(x):
    return x**4+3*x**3-2

a = 0
b = 1

if f(a) * f(b) > 0:
    print("Intervalo no valido")

error = 1e3
X_anterior = 0
n = 1
N = []
Xa = []
Xb = []
Xm = []
Fa = []
Fb = []
Fm = []
E = []
while error > 1e-5:
    m = (a + b) / 2
    X_actual = m
    error = abs(X_anterior - X_actual)
    N.append(n)
    Xa.append(a)
    Xb.append(b)
    Xm.append(m)
    Fa.append(f(a))
    Fb.append(f(b))
    Fm.append(f(m))
    E.append(error)
    if f(a) * f(m) < 0:
         b = m
    else:
         a = m
    X_anterior = X_actual
    n += 1
    d = {
        "N": N,
        "Xa": Xa,
        "Xb": Xb,
        "Xm": Xm,
        "Fa": Fa,
        "Fb": Fb,
        "Fm": Fm,
        "E": E
    }
TT = pd.DataFrame(d)
TT.set_index("N", inplace=True)
print(TT.to_string())
print(". Raíz aproximada:",m)

x = np.linspace(5,-3,101)
plt.plot(x, f(x))
plt.grid()
plt.show()

