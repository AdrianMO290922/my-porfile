# 📚 Ejemplos de Código Responsivo

Ejemplos de buenas prácticas implementadas en tu portafolio.

---

## 1️⃣ Menú Responsive (Header)

```astro
<header id="header" class="fixed top-0 z-50 flex justify-between items-center 
  px-6 md:px-12 py-3 w-full transition-all duration-300">
  
  <!-- Logo -->
  <Logo id="logo" class="size-10 md:size-12 transition-colors" />
  
  <!-- Desktop Menu -->
  <nav id="desktop-nav" class="hidden md:flex gap-4 md:gap-6 text-sm md:text-base">
    <a href="/" class="hover:text-fuchsia-500 transition-colors">Inicio</a>
    <a href="#sobre-mi" class="hover:text-fuchsia-500 transition-colors">Sobre mí</a>
  </nav>
  
  <!-- Mobile Menu Button -->
  <button id="mobile-menu-btn" class="md:hidden text-white">
    <svg class="w-6 h-6">...</svg>
  </button>
</header>

<!-- Mobile Menu (Hidden by default) -->
<nav id="mobile-nav" class="hidden md:hidden">
  <a href="/">Inicio</a>
  <a href="#sobre-mi">Sobre mí</a>
</nav>

<script>
  const mobileMenuBtn = document.querySelector('#mobile-menu-btn');
  const mobileNav = document.querySelector('#mobile-nav');
  
  mobileMenuBtn.addEventListener('click', () => {
    mobileNav.classList.toggle('hidden');
  });
</script>
```

**Breakpoints:**
- `hidden` (todas) → `md:hidden` → Visible solo en móvil
- `hidden md:flex` → Visible solo en desktop
- `size-10 md:size-12` → Escala según pantalla

---

## 2️⃣ Hero Section Responsive

```astro
<section class="min-h-screen flex items-center justify-center py-12 sm:py-16 lg:py-20">
  <div class="flex flex-col lg:flex-row gap-8 sm:gap-12 lg:gap-16 max-w-7xl mx-auto w-full">
    
    <!-- Foto -->
    <div class="flex flex-col items-center gap-6">
      <img 
        class="rounded-full size-40 sm:size-48 lg:size-56 shadow-2xl"
        src="foto.jpg"
        alt="Foto de perfil"
      />
      <h1 class="text-white text-2xl sm:text-3xl lg:text-4xl text-center font-semibold">
        Adrián Martínez
      </h1>
    </div>
    
    <!-- Contenido -->
    <div class="flex flex-col gap-4 sm:gap-6">
      <p class="text-white text-3xl sm:text-4xl lg:text-5xl font-bold">
        Software <span class="text-fuchsia-500">Developer</span>
      </p>
      
      <p class="text-white text-base sm:text-lg lg:text-xl max-w-2xl">
        Descripción con tamaño responsivo
      </p>
      
      <!-- Iconos Sociales -->
      <div class="flex gap-6 sm:gap-8 flex-wrap">
        <a href="#" class="hover:scale-110 transition-transform duration-300">
          <Icon class="size-10 sm:size-12" />
        </a>
      </div>
    </div>
  </div>
</section>
```

**Características:**
- `flex-col lg:flex-row` → Stack en móvil, lado a lado en desktop
- `gap-8 sm:gap-12 lg:gap-16` → Espaciado escala con pantalla
- `size-40 sm:size-48 lg:size-56` → Foto crece según dispositivo
- `text-2xl sm:text-3xl lg:text-4xl` → Título responsivo

---

## 3️⃣ Card de Proyecto

```astro
<div class="h-auto min-h-[480px] sm:min-h-[500px] lg:min-h-[550px]
  flex flex-col w-full sm:w-96 py-6 sm:py-8 px-4 sm:px-6 
  gap-4 sm:gap-6 rounded-2xl sm:rounded-3xl
  bg-gradient-to-br from-white/5 via-white/10 to-white/5
  backdrop-blur-sm hover:from-white/10 hover:via-white/15 hover:to-white/10
  transition-all duration-300">
  
  <!-- Imagen -->
  <img 
    class="w-full h-40 sm:h-52 object-cover rounded-lg sm:rounded-xl 
      shadow-lg hover:shadow-2xl transition-shadow"
    src={imageUrl}
    alt={title}
  />
  
  <!-- Contenido -->
  <div class="text-white text-center flex-grow flex flex-col justify-between">
    <h1 class="text-xl sm:text-2xl lg:text-3xl font-bold leading-tight">
      {title}
    </h1>
    <p class="text-xs sm:text-sm p-2 sm:p-4 opacity-90">
      {description}
    </p>
    
    <!-- Botón -->
    <button class="bg-white/5 border-2 border-white py-2 px-4 
      rounded-lg sm:rounded-xl mt-4 sm:mt-6
      text-sm sm:text-base font-medium
      hover:bg-white hover:text-gray-800
      transition-all duration-300 transform hover:scale-105">
      Ver más
    </button>
  </div>
</div>
```

**Técnicas:**
- `w-full sm:w-96` → Ancho completo en móvil, fijo en desktop
- `min-h-[480px] sm:min-h-[500px] lg:min-h-[550px]` → Altura responsiva
- `flex-grow` + `flex flex-col justify-between` → Botón siempre al final
- Gradiente con hover mejorado

---

## 4️⃣ Grid de Tecnologías

```astro
<section id="tecnologias" class="flex flex-col items-center gap-8 sm:gap-10 
  lg:gap-12 px-4 sm:px-6 lg:px-8 w-full max-w-7xl mx-auto">
  
  <h1 class="text-2xl sm:text-3xl lg:text-4xl text-white font-semibold">
    Tecnologías
  </h1>
  
  <!-- Grid Responsivo -->
  <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-2 
    gap-4 sm:gap-6 lg:gap-8 w-full">
    
    <!-- Card por Categoría -->
    <div class="flex flex-col justify-center items-center 
      gap-6 sm:gap-8 rounded-2xl lg:rounded-3xl
      bg-gradient-to-br from-white/5 via-white/10 to-white/5
      p-6 sm:p-8 hover:scale-105 transition-transform">
      
      <h2 class="text-lg sm:text-xl font-semibold text-white">
        Backend
      </h2>
      
      <!-- Grid de Iconos 3x3 -->
      <div class="grid grid-cols-3 gap-4 sm:gap-6 w-full">
        {technologies.map(tech => (
          <div class="flex flex-col items-center gap-2 sm:gap-3 
            hover:scale-110 transition-transform">
            <Icon class="size-12 sm:size-16" />
            <p class="text-xs sm:text-sm text-white opacity-80">
              {tech.name}
            </p>
          </div>
        ))}
      </div>
    </div>
  </div>
</section>
```

**Responsividad:**
- `grid-cols-1 sm:grid-cols-2 lg:grid-cols-2` → 1 col móvil, 2 desktop
- `gap-4 sm:gap-6 lg:gap-8` → Espacios dinámicos
- `size-12 sm:size-16` → Iconos crecen en pantallas grandes
- `p-6 sm:p-8` → Padding responsivo

---

## 5️⃣ About Section (Hero + Imagen)

```astro
<section id="sobre-mi" class="mt-12 sm:mt-16 lg:mt-20 
  py-12 sm:py-16 lg:py-20 w-full">
  
  <h1 class="text-2xl sm:text-3xl lg:text-4xl text-center 
    font-semibold mb-8 sm:mb-12">
    Sobre mí
  </h1>
  
  <!-- Contenedor Responsivo -->
  <div class="flex flex-col lg:flex-row justify-between items-center 
    gap-8 sm:gap-10 lg:gap-16 px-4 sm:px-6 lg:px-12 max-w-7xl mx-auto">
    
    <!-- Texto -->
    <div class="text-white flex flex-col gap-4 sm:gap-6 w-full lg:w-1/2">
      <h2 class="text-xl sm:text-2xl lg:text-3xl font-semibold">
        ¡Hola! Soy Adrián
      </h2>
      <p class="text-sm sm:text-base lg:text-lg leading-relaxed opacity-90">
        Descripción...
      </p>
    </div>
    
    <!-- Imagen -->
    <div class="w-full lg:w-1/2 flex justify-center">
      <img 
        class="h-64 sm:h-80 lg:h-96 w-full object-cover 
          rounded-2xl lg:rounded-3xl shadow-xl hover:shadow-2xl 
          transition-shadow"
        src="school.jpg"
        alt="ITM"
      />
    </div>
  </div>
</section>
```

**Técnicas:**
- `flex-col lg:flex-row` → Stack vertical en móvil
- `w-full lg:w-1/2` → Ocupa ancho completo en móvil, 50% en desktop
- `gap-8 sm:gap-10 lg:gap-16` → Separación escala con tamaño
- `px-4 sm:px-6 lg:px-12` → Padding horizontal responsivo

---

## 6️⃣ Clases Reutilizables (global.css)

```css
@layer components {
  /* Contenedor principal */
  .container-responsive {
    @apply px-4 sm:px-6 lg:px-8 mx-auto;
  }

  /* Sección con padding */
  .section-padding {
    @apply py-12 sm:py-16 lg:py-20;
  }

  /* Título responsivo */
  .title-main {
    @apply text-2xl sm:text-3xl lg:text-4xl 
      font-bold text-white;
  }

  /* Card responsiva */
  .card-responsive {
    @apply bg-gradient-to-br from-white/5 via-white/10 to-white/5
      rounded-2xl lg:rounded-3xl p-6 sm:p-8 
      backdrop-blur-sm 
      hover:from-white/10 hover:via-white/15 hover:to-white/10 
      transition-all duration-300;
  }

  /* Grid responsivo */
  .grid-responsive {
    @apply grid grid-cols-1 sm:grid-cols-2 
      lg:grid-cols-3 gap-4 sm:gap-6 lg:gap-8;
  }
}
```

**Uso:**
```astro
<div class="container-responsive section-padding">
  <h1 class="title-main">Título</h1>
  <div class="grid-responsive">
    <div class="card-responsive">Contenido</div>
  </div>
</div>
```

---

## 7️⃣ Configuración Tailwind (tailwind.config.js)

```js
export default {
  content: ['./src/**/*.{astro,html,js,jsx,md,mdx,svelte,ts,tsx,vue}'],
  theme: {
    extend: {
      colors: {
        'fuchsia': {
          '500': '#d946ef',
          '600': '#c026d3',
          '700': '#a21caf',
        }
      },
      screens: {
        'xs': '320px',
        'sm': '640px',
        'md': '768px',
        'lg': '1024px',
        'xl': '1280px',
        '2xl': '1536px',
      },
      animation: {
        'fade-in': 'fadeIn 0.5s ease-in',
        'slide-up': 'slideUp 0.5s ease-out',
      },
      keyframes: {
        fadeIn: {
          '0%': { opacity: '0' },
          '100%': { opacity: '1' },
        },
        slideUp: {
          '0%': { transform: 'translateY(20px)', opacity: '0' },
          '100%': { transform: 'translateY(0)', opacity: '1' },
        },
      },
    },
  },
  plugins: [],
}
```

---

## ✨ Tips Importantes

### 1. Orden de Breakpoints
```astro
<!-- ❌ INCORRECTO (desktop-first) -->
<div class="text-5xl md:text-3xl sm:text-xl">

<!-- ✅ CORRECTO (mobile-first) -->
<div class="text-xl sm:text-3xl md:text-4xl lg:text-5xl">
```

### 2. Espaciado Consistente
```astro
<!-- ✅ Buena práctica -->
<div class="px-4 sm:px-6 lg:px-8 py-6 sm:py-8 lg:py-12">
  <div class="gap-4 sm:gap-6 lg:gap-8">
```

### 3. Flexibilidad en Tamaños
```astro
<!-- ✅ Usar clamp() para escalado automático -->
<div class="text-[clamp(1.5rem, 5vw, 3rem)]">
  Título que escala automáticamente
</div>

<!-- O usar breakpoints -->
<div class="text-2xl sm:text-3xl lg:text-4xl">
```

### 4. Efectos en Hover
```astro
<!-- ✅ Combinar múltiples efectos -->
<button class="hover:bg-white hover:text-gray-800
  hover:shadow-lg hover:scale-105
  transition-all duration-300">
  Botón interactivo
</button>
```

---

## 🎯 Resumen de Buenas Prácticas

✅ **Mobile-first**: Estilos base para móvil, luego agregar para pantallas grandes
✅ **Breakpoints semánticos**: sm, md, lg (no magic numbers)
✅ **Componentes reutilizables**: Definir en @layer components
✅ **Espaciado consistente**: Usar escalas (4, 6, 8, etc.)
✅ **Transiciones suaves**: Limitadas a 300ms
✅ **Accesibilidad**: Alt tags, aria-labels, focus states
✅ **Performance**: Purge unused CSS, limitar animaciones

---

**¡Usa estos ejemplos como referencia para futuras mejoras!** 🚀
