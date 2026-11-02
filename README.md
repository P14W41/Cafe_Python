# Cafe_Python
from customtkinter import *

def calcular_total():
    tipo_cafe = opcion_seleccionada_menu_tipo.get()
    tamaño_cafe = opcion_seleccionada_menu_tamaño.get()
    cantidad_cafe = entrada_cantidad.get()

    precio_base = diccionario_precios[tipo_cafe]
    multiplicador_tamaño = diccionario_tamaños[tamaño_cafe]

    total = precio_base * multiplicador_tamaño * int(cantidad_cafe)

    etiqueta_resultado.configure(text=f"Q{total:,.2f}")


diccionario_precios = {
    "Espresso": 16,
    "Americano": 25,
    "Capuccino": 35,
    "Latte": 30,
    "Mocha": 40,
}

diccionario_tamaños = {
    "Pequeño": 1,
    "Mediano": 1.5,
    "Grande": 2,
}

#---------------------------
#COLORES--------------------
COLOR_PRIMARIO = "#101827"
COLOR_PRIMARIO_HOVER = "#101827"
COLOR_FONDO_SECUNDARIO = "#FOF2F5"
COLOR_SECUNDARIO = "#061F4D"
COLOR_SECUNDARIO_HOVER = "#1B263B"
COLOR_TEXTO_CLARO = "#FFFFFF"
COLOR_TEXTO_OBSCURO = "#101827"
COLOR_VERDE = "#10B981"
COLOR_NOSE = "#061297"
COLOR_BLANCO = "#FFFFFF"
COLOR_FONDO= "#E3E5F3"
COLOR_FONDO_OBCURO = "#101827"
COLOR_BORDE = "#E3E5F3"
COLOR_SOMBRA = "#DCDFEF"
COLOR_ASENTO_1= "#03CCFE"
COLOR_ASENTO_2= "#E28DF1"
COLOR_ASENTO_3= "#2BDEDB"
TRANSPARENTE = "transparent"
ALTURA_ESTANDAR_WIDGET = 35

lista_cafes=["Espresso", "Americano", "Capuccino", "Latte", "Mocha"]
lista_tamaños=["Pequeño", "Mediano", "Grande"]

ventana = CTk()
ventana.title("CAFE CIBERNETICO")
ventana.geometry("500x620")
set_appearance_mode("Dark")

ventana.grid_columnconfigure(0, weight=1)
ventana.grid_rowconfigure(0, weight=1)

contenedor_principal = CTkFrame(
    master=ventana,
    fg_color=COLOR_PRIMARIO,
    corner_radius=0,
)

contenedor_principal.grid(
    row=0,
    column=0,
    sticky="nsew",
)

contenedor_principal.grid_columnconfigure(0, weight=1)
contenedor_principal.grid_columnconfigure(1, weight=1)
contenedor_principal.grid_rowconfigure([0,1,2,3,4,5], weight=1)

contenedor_titulo = CTkFrame(
    master=contenedor_principal,
    corner_radius=0,
    fg_color=COLOR_NOSE,
)

contenedor_titulo.grid(
    row=0,
    column=0,
    columnspan=2,
    sticky="nsew",
    padx=5,
)

etiqueta_titulo = CTkLabel(
    master=contenedor_titulo,
    text="CYBER CAFE",
    text_color=COLOR_TEXTO_CLARO,
    font=("Arial", 24, "bold"),
)

etiqueta_titulo.pack(pady=15)

#------------------------------------------------------------------
#ETIQUETAS---------------------------------------------------------

etiqueta_cafe = CTkLabel(
    master=contenedor_principal,
    text="TIPO CAFE",
    height=45,
    corner_radius=0,
    fg_color=COLOR_ASENTO_1,
    text_color=COLOR_TEXTO_CLARO,
    font=("Arial", 14),
)

etiqueta_cafe.grid(
    row=1,
    column=0,
    padx=20,
    sticky="ew"
)

opcion_seleccionada_menu_tipo = StringVar(value="Espresso")

option_menu_cafes = CTkOptionMenu(
    master=contenedor_principal,
    height=ALTURA_ESTANDAR_WIDGET,
    fg_color=COLOR_NOSE,
    corner_radius=0,
    button_color=COLOR_ASENTO_1,
    font=("Arial", 14),
    text_color=COLOR_TEXTO_CLARO,
    text_color_disabled=COLOR_SOMBRA,
    dropdown_text_color=COLOR_TEXTO_CLARO,
    dropdown_fg_color=COLOR_PRIMARIO,
    dropdown_hover_color=COLOR_ASENTO_1,
    hover=True,
    dynamic_resizing=False,
    state="normal",
    variable=opcion_seleccionada_menu_tipo,
    values=lista_cafes,
)

option_menu_cafes.grid(
    row=1,
    column=1,
)

etiqueta_tamaño = CTkLabel(
    master=contenedor_principal,
    text="TAMAÑO",
    height=45,
    corner_radius=0,
    fg_color=COLOR_ASENTO_1,
    text_color=COLOR_TEXTO_CLARO,
    font=("Arial", 14),
)

etiqueta_tamaño.grid(
    row=2,
    column=0,
    padx=20,
    sticky="ew",
)

opcion_seleccionada_menu_tamaño = StringVar(value="Pequeño")

option_menu_tamaños = CTkOptionMenu(
    master=contenedor_principal,
    height=ALTURA_ESTANDAR_WIDGET,
    fg_color=COLOR_NOSE,
    corner_radius=0,
    button_color=COLOR_ASENTO_1,
    font=("Arial", 14),
    text_color=COLOR_TEXTO_CLARO,
    text_color_disabled=COLOR_SOMBRA,
    dropdown_text_color=COLOR_TEXTO_CLARO,
    dropdown_fg_color=COLOR_PRIMARIO,
    dropdown_hover_color=COLOR_ASENTO_1,
    hover=True,
    dynamic_resizing=False,
    state="normal",
    variable=opcion_seleccionada_menu_tamaño,
    values=lista_tamaños,
)

option_menu_tamaños.grid(
    row=2,
    column=1
)

etiqueta_cantidad = CTkLabel(
    master=contenedor_principal,
    text="CANTIDAD",
    height=45,
    corner_radius=0,
    fg_color=COLOR_ASENTO_1,
    text_color=COLOR_TEXTO_CLARO,
    font=("Arial", 14),
)

etiqueta_cantidad.grid(
    row=3,
    column=0,
    padx=20,
    sticky="ew",
)

entrada_cantidad = CTkEntry(
    master=contenedor_principal,
    placeholder_text="Ingrese cantidad",
    height=ALTURA_ESTANDAR_WIDGET,
    corner_radius=0,
    border_width=2,
    border_color=COLOR_ASENTO_1,
    fg_color=COLOR_PRIMARIO,
    text_color=COLOR_TEXTO_CLARO,
    placeholder_text_color=COLOR_SOMBRA,
    justify="center",
    font=("Arial", 14, "bold")
)

entrada_cantidad.grid(
    row=3,
    column=1
)

#---------------------------
#BOTON Y RESULTADO------------

boton_calcular = CTkButton(
    master=contenedor_principal,
    text="CALCULAR TOTAL",
    height=ALTURA_ESTANDAR_WIDGET,
    fg_color=COLOR_ASENTO_1,
    hover_color=COLOR_ASENTO_3,
    text_color=COLOR_TEXTO_CLARO,
    corner_radius=0,
    command=calcular_total,
)

boton_calcular.grid(
    row=4,
    column=0,
    columnspan=2,
    padx=20,
    pady=10,
)

etiqueta_resultado = CTkLabel(
    master=contenedor_principal,
    text="Q0.00",
    height=45,
    text_color=COLOR_TEXTO_CLARO,
    font=("Arial", 22, "bold"),
)

etiqueta_resultado.grid(
    row=5,
    column=0,
    columnspan=2,
)

ventana.bind("<Return>", lambda event: calcular_total())


ventana.mainloop()
