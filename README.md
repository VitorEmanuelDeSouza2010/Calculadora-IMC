# Calculadora-IMC
#Calcula o IMC com o calculo 'peso / (altura * altura)'.

from tkinter import *
from tkinter import ttk
import math

# CORES
co1 = '#000000'
co2 = '#6F9FBD'
co3 = '#38576B'
co4 = '#363434'
co5 = '#424345'

coAP = '#B0C4DE'
coPN = '#4169E1'
coSP = '#98FB98'
coOb1 = '#DAA520'
coOb2 = '#8B4513'
coM = '#800000'

#JANELA
janela = Tk()
janela.title("Calculadora IMC")
janela.geometry("510x500")
janela.configure(bg=co1)
janela.resizable(False, False)

frame_cima = Frame(janela, width=510, height=50, bg= co1, relief="flat")
frame_cima.grid(row=0, column=0, pady=1, padx=0, sticky=NSEW)
frame_baixo = Frame(janela, width=510, height=300, bg= co1, relief="flat")
frame_baixo.grid(row=1, column=0, pady=1, padx=0, sticky=NSEW)

l_altura = Label(frame_cima, text="<Calculadora IMC>", height=1, anchor=NE, font=('Ivy 25'), bg=co1, fg=co2)
l_altura.place(x=120, y=5)

#VARIAVEIS
def calcular():
    altura = float(e_altura.get())
    peso = float(e_peso.get())
    imc = peso / (altura * altura)

    if imc < 18.5:
        label_response.config(text="Abaixo do peso.", bg=co1,fg=coAP)
    elif imc < 24.9:
        label_response.config(text="Peso normal.", bg=co1, fg=coPN)
    elif (imc > 25 and imc < 29.9):
        label_response.config(text="Sobrepeso.",bg=co1, fg=coSP)
    elif (imc > 30 and imc < 34.5):
        label_response.config(text="Obesidade grau 1.", bg=co1, fg=coOb1)
    elif (imc > 35 and imc < 39.9):
        label_response.config(text="Obesidade grau 2.",bg=co1, fg=coOb2)
    elif imc > 40:
        label_response.config(text="Obesidade grau 3 (morbida).",bg=co1, fg=coM)

#INTERFACE E POSIÇÕES
l_altura = Label(frame_baixo, text="altura: ", height=1, anchor=NW, font=('Ivy 10 bold'), bg=co1, fg=co2)
l_altura.place(x=120, y=20)

e_altura = Entry(frame_baixo, width=25, justify='left', font=("", 15), highlightbackground=co1, relief="solid")
e_altura.place(x=120, y=50)

l_peso = Label(frame_baixo, text="Peso: ", height=1, anchor=NW, font=('Ivy 10 bold'), bg=co1, fg=co2)
l_peso.place(x=120, y=95)
e_peso = Entry(frame_baixo,  width=25, justify='left', font=("", 15), highlightbackground=co1, relief="solid")
e_peso.place(x=120, y=130)

label_response = Label(frame_baixo, text='', font=('Ivy 10 bold'), bg=co1)
label_response.place(x=120, y=250)

botao_confirmar = Button(frame_baixo, text="Calcular IMC", width=39, height=2, bg=co2, fg=co1, font=('Ivy 8 bold'), relief=RAISED, overrelief=RIDGE, command=calcular)
botao_confirmar.place(x=120, y=180)

janela.mainloop()
