# 🚀 Guía de Despliegue - Luxury Society SV

## Paso 1: Crear Repositorio en GitHub

1. Ve a [GitHub.com](https://github.com)
2. Inicia sesión o crea una cuenta
3. Click en el botón verde "New" (nuevo repositorio)
4. Nombre del repositorio: `luxury-society-sv`
5. Descripción: "Tienda online de réplicas de lujo premium"
6. Selecciona "Public" (público)
7. ✅ Marca "Add a README file"
8. Click "Create repository"

## Paso 2: Subir Archivos al Repositorio

### Opción A: Usando GitHub Web (Más Fácil)

1. En tu repositorio, click en "Add file" → "Upload files"
2. Arrastra estos archivos:
   - `index.html` (archivo principal)
   - `README.md`
   - `.gitignore`
3. Escribe un mensaje: "Initial commit - Luxury Society SV website"
4. Click "Commit changes"

### Opción B: Usando Git (Línea de Comandos)

```bash
# 1. Inicializar repositorio local
cd /ruta/a/tus/archivos
git init

# 2. Agregar archivos
git add .

# 3. Hacer commit
git commit -m "Initial commit - Luxury Society SV website"

# 4. Conectar con GitHub
git remote add origin https://github.com/TU-USUARIO/luxury-society-sv.git

# 5. Subir archivos
git branch -M main
git push -u origin main
```

## Paso 3: Activar GitHub Pages

1. En tu repositorio, ve a "Settings" (Configuración)
2. En el menú lateral, busca "Pages"
3. En "Source", selecciona:
   - Branch: `main`
   - Folder: `/ (root)`
4. Click "Save"
5. Espera 1-2 minutos

## Paso 4: Ver tu Sitio en Vivo

Tu sitio estará disponible en:
```
https://TU-USUARIO.github.io/luxury-society-sv/
```

Ejemplo: Si tu usuario es "juanperez", será:
```
https://juanperez.github.io/luxury-society-sv/
```

## 📋 Checklist de Archivos

Asegúrate de tener estos archivos en tu repositorio:

- ✅ `index.html` - Página principal
- ✅ `README.md` - Descripción del proyecto
- ✅ `.gitignore` - Archivos a ignorar

## 🔧 Próximos Pasos Recomendados

### 1. Dominio Personalizado (Opcional)

Si tienes un dominio propio (ej: luxurysocietysv.com):

1. En GitHub Pages Settings, agrega tu dominio en "Custom domain"
2. En tu proveedor de dominio, configura estos DNS:
   ```
   A Record: 185.199.108.153
   A Record: 185.199.109.153
   A Record: 185.199.110.153
   A Record: 185.199.111.153
   CNAME: TU-USUARIO.github.io
   ```

### 2. Configurar PayPal

Reemplaza en el código la función `checkout()` con:

```javascript
function checkout() {
    const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
    
    // Crear formulario de PayPal
    const form = document.createElement('form');
    form.method = 'POST';
    form.action = 'https://www.paypal.com/cgi-bin/webscr';
    
    const inputs = {
        'cmd': '_cart',
        'upload': '1',
        'business': 'TU-EMAIL-PAYPAL@ejemplo.com',
        'currency_code': 'USD',
        'return': 'https://TU-SITIO.github.io/gracias.html',
        'cancel_return': 'https://TU-SITIO.github.io/',
    };
    
    // Agregar productos
    cart.forEach((item, index) => {
        inputs[`item_name_${index + 1}`] = item.name;
        inputs[`amount_${index + 1}`] = item.price;
        inputs[`quantity_${index + 1}`] = item.quantity;
    });
    
    // Crear inputs
    for (let key in inputs) {
        const input = document.createElement('input');
        input.type = 'hidden';
        input.name = key;
        input.value = inputs[key];
        form.appendChild(input);
    }
    
    document.body.appendChild(form);
    form.submit();
}
```

### 3. Agregar Google Analytics

Agrega antes de `</head>`:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=TU-ID-GA"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'TU-ID-GA');
</script>
```

### 4. Optimizar SEO

Agrega en el `<head>`:

```html
<!-- SEO Meta Tags -->
<meta name="description" content="Luxury Society SV - Réplicas de lujo premium de Gucci, Louis Vuitton, Balenciaga y más. Envío gratis sobre $150.">
<meta name="keywords" content="réplicas de lujo, Gucci, Louis Vuitton, Balenciaga, ropa de marca">
<meta property="og:title" content="Luxury Society SV - Premium Designer Fashion">
<meta property="og:description" content="Colección exclusiva de réplicas de lujo de las mejores marcas del mundo">
<meta property="og:image" content="URL-DE-TU-LOGO.jpg">
<meta property="og:url" content="https://TU-SITIO.github.io">
```

## 📱 Actualizar el Sitio

Cada vez que hagas cambios:

```bash
# 1. Ver cambios
git status

# 2. Agregar cambios
git add .

# 3. Hacer commit
git commit -m "Descripción de tus cambios"

# 4. Subir a GitHub
git push
```

Los cambios aparecerán en tu sitio en 1-2 minutos.

## 🐛 Solución de Problemas

### El sitio no carga
- Verifica que `index.html` esté en la raíz del repositorio
- Espera 2-5 minutos después de activar GitHub Pages
- Revisa que el repositorio sea público

### Las imágenes no cargan
- Usa URLs completas (https://)
- Verifica que las imágenes estén en el repositorio
- Usa rutas relativas si las imágenes están en tu repo

### Cambios no aparecen
- Limpia caché del navegador (Ctrl + Shift + R)
- Espera 1-2 minutos
- Verifica que el commit se haya subido correctamente

## 📞 Soporte

Si tienes problemas, revisa:
- [Documentación de GitHub Pages](https://docs.github.com/en/pages)
- [Foro de GitHub Community](https://github.community/)

## ✅ Checklist Final

- [ ] Repositorio creado en GitHub
- [ ] Archivos subidos correctamente
- [ ] GitHub Pages activado
- [ ] Sitio funcionando en URL de GitHub Pages
- [ ] Probado en móvil y desktop
- [ ] PayPal configurado (opcional)
- [ ] Dominio personalizado configurado (opcional)
- [ ] Google Analytics agregado (opcional)
- [ ] Contacto actualizado con tus datos reales

¡Tu tienda está lista para vender! 🎉
