# Dinámica de Estilos CSS con JavaScript

Este código permite agregar dinámicamente reglas de estilo CSS en una página web usando JavaScript. Utiliza un array para almacenar las reglas y actualiza un solo elemento `<style>` en el documento. Además, incluye una función que facilita agregar propiedades CSS a un selector específico.

### Descripción de las Funciones:

- **`addStyleRule(rule)`**: Añade una nueva regla de estilo al array `styles` y actualiza el contenido del elemento `<style>` en el documento.
- **`addStyleProperty(selector, property, value)`**: Genera una regla CSS basada en el selector, propiedad y valor, luego la agrega utilizando `addStyleRule`.

El bloque de código `borderAndBoxSizingStyles` aplica un borde rosa de 1px y configura el `box-sizing` para todos los elementos en el documento.

### Código:

~~~javascript
var styles = [];
var styleElement = document.createElement('style');
document.head.appendChild(styleElement);

function addStyleRule(rule) {
    styles.push(rule);
    styleElement.innerHTML = styles.join('\n');
}

function addStyleProperty(selector, property, value) {
    let rule = `${selector} { ${property}: ${value}; }`;
    addStyleRule(rule);
}

const borderAndBoxSizingStyles = `* { border: #E91E63 1px solid !important; box-sizing: border-box; }`;


function showIdsAndClasses() {
    // Recorre todos los elementos del documento
    document.querySelectorAll('*').forEach(element => {
        let id = element.id ? `ID: #${element.id}` : '';
        let classes = element.className ? `Classes: .${element.className.replace(/\s+/g, ' .')}` : '';
        
        if (id || classes) {
            element.style.position = 'relative';
            element.style.border = '1px dashed #E91E63';
            
            let infoDiv = document.createElement('div');
            infoDiv.style.position = 'absolute';
            infoDiv.style.top = '0';
            infoDiv.style.left = '0';
            infoDiv.style.backgroundColor = 'rgba(255, 255, 255, 0.8)';
            infoDiv.style.color = '#333';
            infoDiv.style.fontSize = '10px';
            infoDiv.style.zIndex = '9999';
            infoDiv.style.padding = '2px';
            infoDiv.style.border = '1px solid #E91E63';
            infoDiv.innerText = `${id} ${classes}`;
            element.appendChild(infoDiv);
        }
    });
}
//showIdsAndClasses();

//addStyleRule(borderAndBoxSizingStyles);
~~~
