# HUBSPAIN TOOLS

Este módulo de python3 contiene un set de herramientas utilizadas en los desarrollos de hubspain.com

## Instalación

Puedes instalarlas utilizando pip:
<br>
```bash
pip install hubspain

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

### Existe una versión async de la librería, simplemente debe importarse de la siguiente manera:
```python
from hubspain.generation import async_stablediffusion
```

### License
Este proyecto está autorizado bajo la licencia MIT. Para obtener más información, consulte el archivo de [LICENSE]('https://github.com/flowese/hubspain-tools/blob/main/README.md').
<br>

### Author
Desarrollado por [@flowese]('https://github.com/flowese').
