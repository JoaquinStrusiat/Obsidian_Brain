``` python
users = {
	"1": {"name": "Nazareno", "last_name": "Beauvais", "age": 21},
	"2": {"name": "Joaquin", "last_name": "Strusiat", "age": 22},
	"3": {"name": "Pepito", "last_name": "tal", "age": 24}
}

edades_cuadradas = [];

for userId, data in users.items():
	if data["age"] % 2 == 0:
		edades_cuadradas.append({"name": data["name"], "age": data["age"], "age_square": data["age"] ** 2});

print(edades_cuadradas)

```

