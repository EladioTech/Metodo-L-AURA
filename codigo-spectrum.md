10 REM DECISIONES EN LA CIUDAD (ZX SPECTRUM 48K)
20 REM BASADO EN ALTER EGO Y URBAN UPSTART
30 BORDER 0: PAPER 0: INK 7: CLS 
32 REM CARGA DE IMAGEN DE PRESENTACION
33 BORDER 0: PAPER 0: INK 0: CLS
34 LOAD "" SCREEN$ : REM Esto cargara el archivo 'laura' con las rayas de colores
35 PAUSE 100 : REM Deja la imagen unos segundos en pantalla
36 LET eb=0: LET d=100: LET s=80: LET r=50
37 BORDER 0: PAPER 0: INK 7: CLS : REM Limpia para empezar el texto
40 GO SUB 900: REM PANTALLA TITULO
50 LET escena$="inicio"
60 GO SUB 1000: REM CARGAR ESCENA
70 IF escena$="finalBueno" OR escena$="finalNormal" OR escena$="finalMal" THEN GO TO 500
80 GO TO 60
500 REM FINALES
510 CLS : PRINT AT 5,10;"--- F I N A L ---"
520 IF escena$="finalBueno" THEN PRINT AT 8,5;"FINAL BUENO: Consigues estabilidad."
530 IF escena$="finalBueno" THEN PRINT AT 10,5;"Tu salud mejora, trabajas dignamente"
540 IF escena$="finalBueno" THEN PRINT AT 12,5; "y Laura te da otra oportunidad."
550 IF escena$="finalNormal" THEN PRINT AT 8,5;"FINAL NEUTRO: Sobrevives sin cambios."
560 IF escena$="finalNormal" THEN PRINT AT 10,5;"El psiquiatra te recomienda seguir."
570 IF escena$="finalMal" THEN PRINT AT 8,5;"FINAL MALO: Terminas en la carcel."
580 IF escena$="finalMal" THEN PRINT AT 10,5;"Arruinado y solo. Game Over."
590 PRINT AT 18,5;"Pulsa cualquier tecla para reiniciar"
600 PAUSE 0: RUN 
900 REM SUBRUTINA TITULO
910 CLS : PRINT AT 2,8;"DECISIONES EN LA CIUDAD"
920 PRINT AT 4,6;"Basado en Alter Ego (1986)"
930 PRINT AT 6,6;"Inspirado por el maestro del Spectrum"
940 PRINT AT 10,10;"Pulsa una tecla"
950 PAUSE 0: RETURN 
1000 REM SUBRUTINA CARGAR ESCENA (segun escena$)
1010 IF escena$="inicio" THEN GO SUB 1100
1020 IF escena$="robo" THEN GO SUB 1200
1030 IF escena$="cafe" THEN GO SUB 1300
1040 IF escena$="policia" THEN GO SUB 1400
1050 IF escena$="finalBueno" THEN RETURN 
1060 IF escena$="finalNormal" THEN RETURN 
1070 IF escena$="finalMal" THEN RETURN 
1080 REM FIN
1090 RETURN 
1100 REM ESCENA INICIO
1110 CLS : GO SUB 2000: REM MOSTRAR ESTADO
1120 PRINT AT 4,0;"Alex, treintañero, en paro."
1130 PRINT "El Dr. Mente dice: El tiempo se agota."
1140 PRINT "Ves un coche deportivo con llaves."
1150 PRINT "A tu lado esta Laura, la chica que te gusta."
1160 PRINT AT 12,0;"1-Robar el coche y llevar a Laura"
1170 PRINT "2-Ignorar el coche e invitar a cafe"
1180 PRINT "3-Llamar a la policia"
1190 INPUT a$
1200 IF a$="1" THEN LET escena$="robo": LET d=d+80: LET s=s-20: LET r=r+15: RETURN 
1210 IF a$="2" THEN LET escena$="cafe": LET d=d-5: LET s=s+10: LET r=r+20: RETURN 
1220 IF a$="3" THEN LET escena$="policia": LET d=d+0: LET s=s+15: LET r=r-5: RETURN 
1230 GO TO 1190
1300 REM ESCENA ROBO
1310 CLS : GO SUB 2000
1320 PRINT "Te subes al coche con Laura."
1330 PRINT "Una patrulla os detiene. Robo."
1340 PRINT "Laura se asusta y se baja."
1350 PRINT "Te dan multa y trabajos comunitarios."
1360 PRINT AT 12,0;"1-Aceptar castigo y buscar trabajo"
1370 PRINT "2-Reincidir y robar otra vez"
1380 INPUT a$
1390 IF a$="1" THEN LET escena$="finalNormal": LET d=d-30: LET s=s+10: LET r=r-10: RETURN 
1400 IF a$="2" THEN LET escena$="finalMal": LET d=d+60: LET s=s-40: LET r=r-30: RETURN 
1410 GO TO 1380
1500 REM ESCENA CAFE
1510 CLS : GO SUB 2000
1520 PRINT "Van a un cafe. Laura admira"
1530 PRINT "a la gente honesta. Conectais."
1540 PRINT "El Dr. Mente te felicita."
1550 PRINT "Pero sigues sin dinero."
1560 PRINT AT 12,0;"1-Buscar trabajo fin de semana"
1570 PRINT "2-Pedir dinero prestado a Laura"
1580 INPUT a$
1590 IF a$="1" THEN LET escena$="finalBueno": LET d=d+30: LET s=s+5: LET r=r+10: RETURN 
1600 IF a$="2" THEN LET escena$="finalNormal": LET d=d+20: LET s=s-10: LET r=r-25: RETURN 
1610 GO TO 1580
1700 REM ESCENA POLICIA
1710 CLS : GO SUB 2000
1720 PRINT "Llamas a la policia."
1730 PRINT "El coche era de un narco."
1740 PRINT "Te dan recompensa anonima."
1750 PRINT "Laura ve al soplón, tú ves justicia."
1760 PRINT "El psiquiatra dice que actuaste bien."
1770 PRINT AT 12,0;"1-Invertir en curso de programacion"
1780 PRINT "2-Gastar el dinero en alcohol"
1790 INPUT a$
1800 IF a$="1" THEN LET escena$="finalBueno": LET d=d+50: LET s=s+20: LET r=r-5: RETURN 
1810 IF a$="2" THEN LET escena$="finalMal": LET d=d-40: LET s=s-30: LET r=r-5: RETURN 
1820 GO TO 1790
2000 REM SUBRUTINA MOSTRAR ESTADO
2010 PRINT AT 0,0;"Dinero:";d;"   Salud:";s;"   Relacion:";r
2020 PRINT AT 0,25;"Escena: ";escena$
2030 RETURN 