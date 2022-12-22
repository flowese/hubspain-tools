# HUBSPAIN TOOLS

Este módulo de python3 contiene un set de herramientas utilizadas en los desarrollos de hubspain.com

## Instalación

Puedes instalarlas utilizando pip:
<br>
```bash
pip install asyncio aiohttp requests PIL base64

```

<br>
Una vez instaladas las dependencias, puedes utilizar el módulo importándolo en tu código de la siguiente forma:<br>
<br>


Opción 1: Parámetros individuales basicos.

```python
from hubspain.generation import stablediffusion

images = stablediffusion(hsp_apikey,prompt="a cat", height=512, width=512, steps=60, cfg_scale=7, seed="2")

# guarda las imágenes generadas en el directorio actual
for i, image_bytes in enumerate(images):
    image_bytes.save(f"image{i}_opcion1.png")

```
<br>
Opción 2: Diccionario de parámetros avanzado.

```python
    submit_dict = {
        "prompt": "a cat",
        "params": {
            "sampler_name": "k_euler_a",
            "n": 1,
            "width": int(512),
            "height": int(512),
            "steps": 60,
            "cfg_scale": 7,
            "denoising_strength": 0.75,
            "seed": str(""),
            "post_processing": ["GFPGAN"],
        },
        "nsfw": False,
        "censor_nsfw": False,
        "trusted_workers": True,
        "models": [models_list[1]],
    }

    # Lanzamos la petición con el diccionario de parámetros
    images = stablediffusion(hsp_apikey,submit_dict=submit_dict)

    # guarda las imágenes en el directorio actual
    for i, image_bytes in enumerate(images):
        image_bytes.save(f"image{i}_opcion2.png")
```

### License
This project is licensed under the MIT license. For more information, see the [LICENSE]('https://github.com/flowese/hubspain-tools/blob/main/README.md') file.
<br>

### Author
Developed by [@flowese]('https://github.com/flowese').
