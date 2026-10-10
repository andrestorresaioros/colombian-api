# Colombian API — Procesamiento de datos abiertos

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js_18+-339933?style=flat&logo=nodedotjs&logoColor=white)

Solución a una prueba técnica de procesamiento de datos: consumo de la API pública [api-colombia.com](https://api-colombia.com/) y agrupamiento de la información de presidentes, atracciones turísticas y aeropuertos de Colombia.

## Consultas implementadas

| Comando | Función | Resultado |
|---|---|---|
| `npm run presidentes` | `groupPresidentsByParty` | Presidentes agrupados por partido político, ordenados de mayor a menor número de presidentes. |
| `npm run atracciones` | `groupTouristicAttractionsByDepartmentCity` | Atracciones turísticas agrupadas por departamento y ciudad, con su conteo. |
| `npm run aeropuertos` | `groupAirportByDepartmentCity` | Aeropuertos agrupados por departamento y ciudad, con su conteo. |
| `npm run regiones` | `groupAirportsByRegionDepartmentCityType` | Conteo de aeropuertos anidado por región → departamento → ciudad → tipo. |

Todas las funciones usan `fetch` con `async/await` y procesan los datos con `reduce`, cruzando entidades (departamentos y regiones) para resolver los nombres.

## Ejecución

Requiere Node.js 18 o superior (incluye `fetch` de forma nativa). No hay dependencias que instalar.

```bash
npm run regiones          # o: node prueba.js regiones
```

Sin argumento, `npm start` ejecuta la consulta de regiones.

## Ejemplo de salida

[`salidas/aeropuertos_por_region_departamento_ciudad_tipo.json`](salidas/aeropuertos_por_region_departamento_ciudad_tipo.json) contiene el resultado de la agrupación por región:

```json
{
  "region": {
    "Andina": {
      "departamento": {
        "Antioquia": {
          "ciudad": {
            "Rionegro": { "tipo": { "Militar": 1, "Internacional": 1 } }
          }
        }
      }
    }
  }
}
```

## Autor

**César Andrés Torres Bernal** · [GitHub](https://github.com/andrestorresaioros) · [LinkedIn](https://www.linkedin.com/in/andr%C3%A9s-torres10)

## Licencia

Distribuido bajo la licencia MIT. Consulta [LICENSE](LICENSE).
