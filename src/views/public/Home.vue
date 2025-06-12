<template>
  <HeroCarousel :slides="heroSlides" @cta="handleCtaClick" />

  <RoomsGrid :rooms="rooms" />

  <!-- <ServicesGrid :services="services" /> -->

  <AboutSection
    :image="aboutImage"
    :title="aboutTitle"
    :text="aboutText"
    :values="aboutValues"
  />

  <TestimonialCarousel :testimonials="testimonials" />

  <FooterSection @subscribe="onSubscribe" />
</template>

<script setup>
import { useRouter } from "vue-router";
import HeroCarousel from "@/components/home/HeroCarousel.vue";
import WhyUsCards from "@/components/home/WhyUsCards.vue";
import ServicesGrid from "@/components/home/ServicesGrid.vue";
import RoomsGrid from "@/components/rooms/RoomsGrid.vue";
import TestimonialCarousel from "@/components/home/TestimonialCarousel.vue";
import SecondaryCTA from "@/components/home/SecondaryCTA.vue";
import AboutSection from "@/components/home/AboutSection.vue";
import FooterSection from "@/components/home/FooterSection.vue";

const router = useRouter();

// Datos de habitaciones para mostrar en la grid
const rooms = [
  {
    id: 1,
    name: 'HABITACION SIMPLE',
    image: '/images/WhatsApp Image 2025-05-30 at 11.28.39.jpeg',
    price: 30.00,
    size: 25,
    capacity: 2,
    bedType: 'Cama doble',
    description: 'Habitación acogedora con todas las comodidades necesarias para una estancia agradable.',
    amenities: ['WiFi',],
    isPopular: true,
    isFavorite: false
  },
  {
    id: 2,
    name: 'HABITACION CON BAÑO PRIVADO',
    image: '/images/651854110.jpg',
    price: 60.00,
    size: 35,
    capacity: 2,
    bedType: 'Cama king',
    description: 'Habitación espaciosa con vistas panorámicas. Equipada con minibar, escritorio y zona de estar. Perfecta para viajeros de negocios y placer.',
    amenities: ['WiFi', 'TV', 'Aire acondicionado', 'Minibar', 'Caja fuerte', 'Baño privado'],
    isPopular: false,
    isFavorite: false
  },
  {
    id: 3,
    name: 'HABITACIONES MATRIMONIALES',
    image: '/images/WhatsApp Image 2025-05-30 at 19.27.04.jpeg',
    price: 80.00,
    size: 5,
    capacity: 2,
    bedType: 'Cama king + sofá cama',
    description: 'habuitacion elegante con dormitorio. Ofrece un espacio perfecto para relajarse después de un día de turismo o negocios.',
    amenities: ['WiFi', 'TV', 'Aire acondicionado', 'Minibar', 'Baño privado',],
    isNew: true,
    isFavorite: false
  },
  {
    id: 4,
    name: 'HABIATACION DOBLE',
    image: '/images/WhatsApp Image 2025-05-30 at 11.28.37.jpeg',
    price: 40.00,
    size: 60,
    capacity: 2,
    bedType: 'Cama king + 2 camas individuales',
    description: 'Amplia habitacion con dormitorio, Ideal para  estadías prolongadas. ',
    amenities: ['WiFi', 'TV', 'Aire acondicionado',, 'Servicio de habitaciones'],
    isPopular: true,
    isFavorite: false
  },
  {
    id: 5,
    name: 'Habitación Familiar',
    image: '/images/651854085.jpg',
    price: 70.00,
    size: 5,
    capacity: 4,
    bedType: '2 camas dobles',
    description: 'Habitación espaciosa diseñada para familias. Incluye zona de juegos para niños y todas las comodidades para una estancia confortable.',
    amenities: ['WiFi', 'TV', 'Aire acondicionado', 'Minibar', 'Baño privado', 'Parking'],
    isNew: false,
    isFavorite: false
  },
  {
    id: 6,
    name: 'PROMOCIONES FECHAS FESTIVAS',
    image: '/images/WhatsApp Image 2025-05-30 at 19.19.07.jpeg',
    price: 50.00,
    size: 30,
    capacity: 2,
    bedType: 'Cama doble',
    description: 'Habitación diseñada para ofrecer accesibilidad total. Cuenta con baño adaptado y todas las facilidades para una estancia cómoda.',
    amenities: ['WiFi', 'TV', 'Aire acondicionado', 'Baño adaptado', 'Parking'],
    isNew: false,
    isFavorite: false
  }
];

const heroSlides = [
  {
    image: "/images/hotel-lobby.jpg",
    title: "Bienvenido al Hospedaje Bernett",
    subtitle: "Disfruta de una experiencia única en un entorno de lujo y confort",
    //ctaText: "Reserva ahora",
    //btnVariant: "btn-primary" 
  },
  {
    image: "/images/hotel-pool.jpg",
    title: "Relájate y disfruta Una",
    subtitle: "Instalaciones de primera clase para una estancia inolvidable",
    //ctaText: "Descubre más",
    alignment: "text-end",
    //btnVariant: "btn-light"
  },
  {
    image: "/images/hotel-restaurant.jpg",
    title: "Experiencia que Nunca Olvidaras",
    subtitle: "Puede Adquirir Variedad de Productos de Nuestra Tienda",
    //ctaText: "Ver menús",
    alignment: "text-start",
    //btnVariant: "btn-outline-light"
  },
  {
    image: "/images/hotel-spa.jpg",
    title: "Relájate y rejuvenece",
    subtitle: "Disfruta de nuestros servicios de spa y bienestar",
    //ctaText: "Ver tratamientos",
    alignment: "text-center",
    //btnVariant: "btn-secondary"
  }
];  

// Datos para la sección de testimonios
const testimonials = [
  {
    name: "Sucursal 1",
    image: "/images/WhatsApp Image 2025-05-30 at 19.46.20.jpeg",
    text: "Dir: Villa Caluyo D #784 Entre Calle 5 y 6.",
    rating: 5
  },
  {
    name: "Sucursal 2",
    image: "/images/WhatsApp Image 2025-05-30 at 19.45.49.jpeg",
    text: "Zona Cruce Villa Adela, Av. Ladislao Cabrera, calle 1 N.º 2094 .",
    rating: 4.5
  },
  {
    name: "Orlando Quispe (propietario)",
    image: "/images/WhatsApp Image 2025-05-30 at 19.41.13.jpeg",
    text: "comunicate con los numeros en pantalla 70165207-65138908.",
    rating: 8
  }
];

// Datos para la sección de CTA secundaria
const secondaryCtaTitle = "¿Listo para tu próxima aventura?";
const secondaryCtaSubtitle = "Reserva ahora y obtén un descuento exclusivo.";
const secondaryCtaText = "Reserva ahora";

// Datos para la sección "Sobre nosotros"
const aboutImage = "/images/WhatsApp Image 2025-05-30 at 14.26.29.jpeg";
const aboutTitle = "Acerca de Nosotros";
const aboutText = "En el HOSTAL BERNETT,Ofrecer un servicio de calidad, accesible y disponible las 24 horas en El Alto en nuestras dos sucursales con parqueo gratis, con atención respetuosa y culturalmente inclusiva, enfocada en el bienestar del huésped, y con proyección de crecimiento mediante nuevas sucursales.";
const aboutValues = [
  { icon: "fa-solid fa-star", text: "Calidad excepcional" },
  { icon: "fa-solid fa-heart", text: "Atención personalizada" },
  { icon: "fa-solid fa-leaf", text: "Sostenibilidad" }
];

// Métodos
function handleCtaClick(slide) {
  if (slide.ctaText === "Reserva ahora") {
    goRegister();
  } else if (slide.ctaText === "Descubre más") {
    router.push("/services");
  } else if (slide.ctaText === "Ver menús") {
    router.push("/restaurant");
  } else if (slide.ctaText === "Ver tratamientos") {
    router.push("/spa");
  }
}

function goRegister() {
  router.push("/register");
}

function onSubscribe(email) {
  console.log(`Usuario suscrito con el correo: ${email}`);
}
</script>