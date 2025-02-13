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
### Resultado final
Elegir un vehículo que cumpla con todos esos requisitos puede ser algo desafiante, pero te puedo ofrecer algunos consejos para ayudarte en tu búsqueda.

1. **Modelo sugerido: Honda Fit 2015**
   - **Consumo de combustible:** El Honda Fit es conocido por su eficiencia de combustible. La versión 2015 tiene un buen rendimiento en carretera y ciudad.
   - **Espacio:** Es un hatchback subcompacto pero ofrece un sorprendente espacio interior y flexibilidad con su configuración de asientos Magic Seat.
   - **Precio:** En el mercado de autos usados, es posible encontrar un Honda Fit 2015 dentro de un rango de precios que podría ajustarse a tu presupuesto, pero siempre es bueno verificar en diversas fuentes como concesionarios de autos usados, clasificados en línea o subastas.
   - **Color negro:** El color puede ser un desafío adicional, pero es uno de los colores más comunes, por lo que es más probable encontrarlo.

2. **Dónde buscar:**
   - Plataformas en línea como Autotrader, Cars.com, o Craigslist.
   - Concesionarios locales de autos usados.
   - Considera expandir tu búsqueda geográficamente para tener más opciones.

3. **Verificación:**
   - Asegúrate de revisar el historial del vehículo a través de servicios como Carfax o AutoCheck.
   - Realiza una inspección mecánica antes de hacer la compra.

Recuerda que los precios pueden variar significativamente dependiendo de la región, el estado del vehículo y el kilometraje. Es importante mantener la flexibilidad y paciencia durante tu búsqueda para encontrar el auto que mejor se adapte a tus necesidades y presupuesto.

https://oaidalleapiprodscus.blob.core.windows.net/private/org-IXDq1dCDgarIuZWhdHKtZkAE/user-SEt9Y5ffv9NZbD7CqPSykGWk/img-OkbRR6LbTPDNsjgqVLYlNKan.png?st=2025-02-13T10%3A03%3A18Z&se=2025-02-13T12%3A03%3A18Z&sp=r&sv=2024-08-04&sr=b&rscd=inline&rsct=image/png&skoid=d505667d-d6c1-4a0a-bac7-5c84a87759f8&sktid=a48cca56-e6da-484e-a814-9c849652bcb3&skt=2025-02-13T11%3A03%3A18Z&ske=2025-02-14T11%3A03%3A18Z&sks=b&skv=2024-08-04&sig=bVyAU5tPNlSYz0ij55UacfaY9QtwTd9KVJei4oGjEnU%3D

![colab](https://github.com/user-attachments/assets/ce16d2a1-05cb-4ad5-a54f-ab3276a6a87a)

### Resultado final
Gracias al uso de inteligencia artificial pudimos resolver la problematica de muchos que es que automovil elegir, la cual nos brinda datos especificos del modelo y sus distintas variantes etc

los resultados por parte del chat gpt fueron muy precisos mientras que del lado de DALL-E 3 algunas veces genero una imagen un poco distinta a lo que se pedia mediante el prompt, pero siempre ayudaron mucho a tener una idea del automovil elegido 


