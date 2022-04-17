# Consumo-de-SWAPI
Utilizar la API disponible del proyecto SWAPI, con el fin de responder a las siguientes preguntas: a) ¿En cuántas películas aparecen planetas cuyo clima sea árido?, b) ¿Cuántos Wookies aparecen en la sexta película?, c) ¿Cuál es el nombre de la aeronave más grande en toda la saga?
import requests  
import json


print("SOLICITANDO INFORMACION DE INTERNET")
print("espere....\n") 
url1 = 'https://swapi.it/api/planets'
url2 = 'https://swapi.it/api/species'
url3 = 'https://swapi.it/api/films'
url4 = 'https://swapi.it/api/starships'



response1 = requests.get(url1)
response2 = requests.get(url2) 
response3 = requests.get(url3) 
response4 = requests.get(url4)



print("a) ¿En cuántas películas aparecen planetas cuyo clima sea árido?\n")

if response1.status_code ==200:

	respuesta = response1.json()

	resultado = respuesta['results']
	print("PLANETAS CUYO CLIMA ES ARIDO: \n")
	for j in resultado:
		m=j['name']
		x=j['climate']
		# print(x)

		if x == 'arid':
			print("Planeta: " + m + "\tClima: "+ x)

	print("\nCantidad de peliculas en la que aparece: ")
	cfilms=resultado[0]
	print(len(cfilms['films']))
	print()
	for h in cfilms['films']:
		print(h)

print("\nb) ¿Cuántos Wookies aparecen en la sexta película?\n")
			

if response2.status_code ==200:
		respuesta=response2.json()
		resultado= respuesta['results']
		pelicula= response3.json()
		
		print("NOMBRE")
		wookie=resultado[2]

		print(wookie['name'])

		print("\nCANTIDAD TOTAL: ")
		print(len(wookie['people']))
		print("\nQUIENES: ")
		for i in wookie['people']:
			print(i)

		res=pelicula['results']
		sexta=res[2]
		
		print("\nCUAL APARECE EN " + sexta['title'])

		for k in sexta['characters']:
			if k=='https://www.swapi.it/api/people/13' or k=='https://www.swapi.it/api/people/80':
				print(k)

print("\nc) ¿Cuál es el nombre de la aeronave más grande en toda la saga?\n")

if response4.status_code ==200:
	respuesta=response4.json()
	resultado= respuesta['results']

	for o in resultado:
		ns=o['name']
		t=o['length']

		if t == '120000':
			print("La nave mas grande es: " + ns + " -Siendo su tamaño de: "+t)
