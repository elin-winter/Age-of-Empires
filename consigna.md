Age of Empires II es un videojuego de estrategia en tiempo real para computadoras personales desarrollado en un principio por Ensemble Studios y más tarde por Skybox Labs. Fue lanzado a mediados de 1999 y es el segundo título que compone la serie Age of Empires.
Nos contratan para hacer una nueva versión del juego en el lenguaje Prolog ya que este es ultra mainstream.
Para empezar, tenemos jugadores de quienes sabemos su nombre, su rating y su civilización favorita. También sabemos qué unidades (y cuántas), recursos (Madera, Alimento, Oro) y edificios (y cuántos) tiene cada jugador.

De las unidades sabemos que pueden ser militares o aldeanos.
● De los militares sabemos su tipo, cuántos recursos cuesta y a qué categoría pertenece.
● De los aldeanos sabemos su tipo y cuántos recursos por minuto produce. Su categoría es aldeano.
% militar(Tipo, costo(Madera, Alimento, Oro), Categoria).
militar(espadachin, costo(0, 60, 20), infanteria).
militar(arquero, costo(25, 0, 45), arqueria).
militar(mangudai, costo(55, 0, 65), caballeria).
militar(samurai, costo(0, 60, 30), unica).
militar(keshik, costo(0, 80, 50), unica).
militar(tarcanos, costo(0, 60, 60), unica).
militar(alabardero, costo(25, 35, 0), piquero).
% ... y muchos más tipos pertenecientes a estas categorías.
% aldeano(Tipo, produce(Madera, Alimento, Oro)).
aldeano(lenador, produce(23, 0, 0)).
aldeano(granjero, produce(0, 32, 0)).
aldeano(minero, produce(0, 0, 23)).
aldeano(cazador, produce(0, 25, 0)).
aldeano(pescador, produce(0, 23, 0)).
aldeano(alquimista, produce(0, 0, 25)).
% ... y muchos más también

% ...jugador(Nombre, Rating, Civilizacion).
jugador(juli, 2200, jemeres).
jugador(aleP, 1600, mongoles).
jugador(feli, 500000, persas).
jugador(aleC, 1723, otomanos).
jugador(ger, 1729, ramanujanos).
jugador(juan, 1515, britones).
jugador(marti, 1342, argentinos).
% ... y muchos más también

% ...tiene(Nombre, QueTiene).
tiene(aleP, unidad(samurai, 199)).
tiene(aleP, unidad(espadachin, 10)).
tiene(aleP, unidad(granjero, 10)).
tiene(aleP, recurso(800, 300, 100)).
tiene(aleP, edificio(casa, 40)).
tiene(aleP, edificio(castillo, 1)).
tiene(juan, unidad(carreta, 10)).
% ... y muchos más también

De los edificios sabemos su tipo y el costo de construcción.
% edificio(Edificio, costo(Madera, Alimento, Oro)).
edificio(casa, costo(30, 0, 0)).
edificio(granja, costo(0, 60, 0)).
edificio(herreria, costo(175, 0, 0)).
edificio(castillo, costo(650, 0, 300)).
edificio(maravillaMartinez, costo(10000, 10000, 10000)).
% ... y muchos más también
Crear los siguientes predicados de manera que sean totalmente inversibles:
1) Definir el predicado esUnAfano/2, que nos dice si al jugar el primero contra el segundo, la diferencia de
rating entre el primero y el segundo es mayor a 500.
2) Definir el predicado esEfectivo/2, que relaciona dos unidades si la primera puede ganarle a la otra según
su categoría, dado por el siguiente piedra, papel o tijeras:
a- La caballería le gana a la arquería.
b- La arquería le gana a la infantería.
c- La infantería le gana a los piqueros.
d- Los piqueros le ganan a la caballería.
Por otro lado, los Samuráis son efectivos contra otras unidades únicas (incluidos los samurái).
Los aldeanos nunca son efectivos contra otras unidades.

3) Definir el predicado alarico/1 que se cumple para un jugador si solo tiene unidades de infantería.
4) Definir el predicado leonidas/1, que se cumple para un jugador si solo tiene unidades de piqueros.
5) Definir el predicado nomada/1, que se cumple para un jugador si no tiene casas.
6) Definir el predicado cuantoCuesta/2, que relaciona una unidad o edificio con su costo. De las unidades
militares y de los edificios conocemos sus costos. Los aldeanos cuestan 50 unidades de alimento. Las
carretas y urnas mercantes cuestan 100 unidades de madera y 50 de oro cada una.
7) Definir el predicado produccion/2, que relaciona una unidad con su producción de recursos por minuto.
De los aldeanos, según su profesión, se conoce su producción. Las carretas y urnas mercantes producen
32 unidades de oro por minuto. Las unidades militares no producen ningún recurso, salvo los Keshiks, que
producen 10 de oro por minuto.
8) Definir el predicado produccionTotal/3 que relaciona a un jugador con su producción total por minuto de
cierto recurso, que se calcula como la suma de la producción total de todas sus unidades de ese recurso.
9) Definir el predicado estaPeleado/2 que se cumple para dos jugadores cuando no es un afano para
ninguno, tienen la misma cantidad de unidades y la diferencia de valor entre su producción total de
recursos por minuto es menor a 100 . ¡Pero cuidado! No todos los recursos valen lo mismo: el oro vale 1
cinco veces su cantidad; la madera, tres veces; y los alimentos, dos veces.
10) Definir el predicado avanzaA/2 que relaciona un jugador y una edad si este puede avanzar a ella:
a) Siempre se puede avanzar a la edad media.
b) Puede avanzar a edad feudal si tiene al menos 500 unidades de alimento y una casa.
c) Puede avanzar a edad de los castillos si tiene al menos 800 unidades de alimento y 200 de oro.
También es necesaria una herrería, un establo o una galería de tiro.
d) Puede avanzar a edad imperial con 1000 unidades de alimento, 800 de oro, un castillo y una universidad. 