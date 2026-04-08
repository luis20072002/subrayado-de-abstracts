# Reto 3: Subrayado de abstracts

Proyecto desarrollado para resaltar palabras clave dentro de abstracts de artículos científicos sobre LLMs en educación. El resultado se presenta como un dashboard interactivo en Quarto.

**Autores**

- Santiago José Cuesta Maza — T00082473
- Valeria Estefanía Berrio Payares — T00082178
- Luis Eduardo Mendoza Angulo — T00082297
- Deiner de Jesús Gonzalez Paredes — T00082648
- Danna Valentina Zuluaga Hernández — T00082548

---

## Descripción

A partir de una base de datos de artículos científicos, el proyecto identifica y resalta visualmente dos tipos de términos dentro de los abstracts:

- **Inclusión** (fondo amarillo): palabras que indican uso de un LLM — `GPT`, `BERT`, `T5`, `LLaMA`, `PaLM`, `Gemini`, `Mistral`, `DeepSeek`, `LLMS`.
- **Exclusión** (fondo rojo): palabras que indican ausencia de uso de LLM — `No LLM usage`, `NLP`, `machine learning`, `IA Y familia`.

---

## Estructura del proyecto

```
.
├── reto-modi.qmd            # Dashboard principal de Quarto
├── styles.css               # Estilos personalizados del dashboard
└── 2_base_maestra_LIMPIA.csv  # Base de datos de artículos científicos
```

---

## Requisitos

- [Quarto](https://quarto.org/) >= 1.4
- Python >= 3.9
- Paquetes Python:

```
pandas
IPython
```

Instalación de dependencias:

```bash
pip install pandas ipython
```

---

## Uso

Renderizar el dashboard con:

```bash
quarto render reto-modi.qmd
```

O en modo previsualización en vivo:

```bash
quarto preview reto-modi.qmd
```

---

## Funcionamiento del código

El núcleo del proyecto es la clase `ResaltadorDeAbstracts`, que recibe las listas de palabras al instanciarse y expone un método principal para renderizar todos los artículos.

```python
resaltador = ResaltadorDeAbstracts(
    terminos_inclusion=palabras_inclusion,
    terminos_exclusion=palabras_exclusion,
)
resaltador.renderizar_todos(df)
```

Internamente usa `re.compile` con la bandera `re.IGNORECASE` para encontrar coincidencias sin importar mayúsculas, y `patron.sub()` con una función lambda para envolver cada coincidencia en una etiqueta `<mark>` con el estilo CSS correspondiente. El resultado se renderiza con `IPython.display.HTML`.

---

## Licencia

Este proyecto está bajo la licencia MIT. Ver el archivo `LICENSE` para más detalles.
