# Zadaca-tajmer 
Да се иницијализира компонентата 8155/56 така да RAM-от зафаќа простор 4800h–48FFh. Портата А да се иницијализира како стробирана влезна порта, а B како обична излезна. Тајмерот брои поворка од кратки импулси со T = 1ms. (f=4MHZ).

Resenie:

А15 А14 А13 А12 А11

32к 16к 8к 4к 2к

0 1 0 0 1
CSR 01001 000

PA 01001 001

PB 01001 010

PC 01001 011

TLSB 01001 100

TMSB 01001 101

T=0,25 microsec, Ts = 0,5 microsec; 1 ms = 2000 * 0,5 microsec; 2000 = 7*256+208

TMSB 11000111

TLSB 11010000

CSR 11010110

MVI A, 208d        CSR EQV 01001000

OUT TLSB           TMSB EQV 01001101

MVI A, 199d        TLSB EQV 01001100

OUT TMSB

MVI A, D6h

OUT CSR

END
 ![Screenshot (1)](https://github.com/TrajceStudent/Zadaca-tajmer/blob/main/Diagram.png)
