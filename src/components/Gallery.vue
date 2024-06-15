<template>
    <section class="gallery-container" ref="gallerySection">
      <div class="section-header">
        <div class="section-header-small">
          <h5>Gallery</h5>
          <div class="header-line"></div>
        </div>
        <h2>View Our <span class="highlight">Gallery</span></h2>
      </div>
      <div class="gallery-wrapper">
        <div class="gallery-image" v-for="(image, index) in images" :key="index">
          <img :src="image" alt="Gallery Image" @click="openModal(image)" />
        </div>
      </div>
      <!-- Modal for enlarged image -->
      <transition name="modal-fade">
        <div v-if="modalImage" class="modal" @click="closeModal">
          <img
            :src="modalImage"
            alt="Enlarged Gallery Image"
            class="modal-content"
          />
        </div>
      </transition>
    </section>
  </template>
  
  <script>
  import image1 from "../assets/images/gallery_1.png";
  import image2 from "../assets/images/gallery_2.png";
  import image3 from "../assets/images/gallery_3.png";
  import image4 from "../assets/images/gallery_4.png";
  import image5 from "../assets/images/gallery_5.png";
  import image6 from "../assets/images/gallery_6.png";
  
  export default {
    name: "GalleryComponent",
    data() {
      return {
        images: [image1, image2, image3, image4, image5, image6],
        modalImage: null,
      };
    },
    methods: {
      openModal(image) {
        this.modalImage = image;
      },
      closeModal() {
        this.modalImage = null;
      }
    }
  };
  </script>
  
  <style scoped>
  .gallery-container {
    padding: 120px 64px;
    display: flex;
    flex-direction: column;
    gap: 40px;
  }
  
  .gallery-wrapper {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 16px;
    width: 100%;
  }
  
  .gallery-image img {
    width: 100%;
    height: 200px; /* Set a uniform height */
    object-fit: cover; /* Maintain aspect ratio, fill the space */
    display: block;
    border-radius: 8px;
    cursor: pointer; /* Indicate that the images are clickable */
  }

  .gallery-image img:hover {
    transform: scale(1.05);
    transition: transform 0.5s;
  }
  
  /* Modal styling */
  .modal {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    z-index: 1000;
  }
  
  .modal-content {
    max-width: 90%;
    max-height: 90%;
    border-radius: 8px;
  }
  
  /* Transition effects */
  .modal-fade-enter-active, .modal-fade-leave-active {
    transition: opacity 0.5s;
  }
  .modal-fade-enter, .modal-fade-leave-to {
    opacity: 0;
  }
  
  @media (max-width: 768px) {
    .gallery-container {
      padding: 32px;
    }
  }
  </style>  