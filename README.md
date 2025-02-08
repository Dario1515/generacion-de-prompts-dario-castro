# Preentrega 1 Dario Castro – Comisión 76165
## Nombre del proyecto: Buscador de vehículos a medida

### Problemática a resolver: En el mundo de los vehículos existen millones de alternativas, ya sea por precio, modelos etc. Lo cual se vuelve un poco tedioso encontrar un vehículo indicado el cual tenga lo que el cliente busca  
La implementación de una herramienta con IA facilitara el poder ingresar los datos que el cliente busca, como marca, combustible, precio, tamaño, color etc y el programa le indicara cual vehículo se adapta a sus necesidades 

```python 

import openai
#Configurando la API_KEY
openai.api_key = "inserte api key"

# LLamando a la API para generar nuestro chat

response = openai.ChatCompletion.create(
    model="gpt-4o",
    messages=[
        {"role": "user", "content": "Quiero que me ayudes a elegir un vehículo que tenga bajo consumo, sea amplio, año 2015, Honda, precio menor a 9000 dolares, color negro"}
    ]
)

# Imprimir la respuesta del asistente
print(response["choices"][0]["message"]["content"])

```

El uso de esta herramienta no tendrá un gasto elevado ya que solo el prompt tiene un total de 25 tokens y el precio del millón de tokens usados es de 2,5 dólares lo que daría unos 40.000 usos, suponiendo que se necesite una búsqueda un poco más exhaustiva se podría suplicar el costo de tokens

### Herramientas y Tecnologías 

1. **ChatGPT (GPT-4o):** Se utilizará para ayudar al comprador a encontrar el auto que sea mas acorde a sus gustos utilizando su motor de búsqueda para garantizar la elección adecuada 

2. **DALL-E 3:** Este modelo será utilizado para generar imágenes visuales que representen los vehículos seleccionados por los usuarios

3. **Python:** El lenguaje de programación utilizado para implementar el código, debido a su facilidad de uso y su amplia compatibilidad con las APIs de OpenAI.

4. **Técnica de Prompting:** Se implementará one-shot prompting, donde se proporcionara en un solo prompt los datos necesarios para generar la busqueda


## Generar una imagen visual con DALL-E 3
Para gener la imagen que buscamos usaremos dall-e 3 el cual nos permite ingresar los datos brindados por chat gpt y realizar una busqueda del vehiculo el cual buscamos anteriormente y poder visualizarlo

## Prompt para Generación de Imágenes (Texto-Imagen)

Para la visualización de la agenda, generaremos un prompt como el siguiente:

```python 
# Generar una imagen visual con DALL-E 3
cliente_imagen = openai.Image.create(
    prompt="en base al resultado anterior dado por chat gpt quiero que generes una imagen del vehiculo mostrado.",
    size="1024x1024"
)

# Mostrar la imagen generada
print(cliente_imagen['data'][0]['url'])
```
