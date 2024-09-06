<template>
  <div class="form-wrapper">
    <div class="form-container">
      <h1>Formulario de Registro</h1>
      <form @submit.prevent="handleSubmit" class="form">
        <div class="form-group">
          <label for="nombre">Nombre completo</label>
          <input v-model="formData.nombre" type="text" id="nombre" placeholder="Ingresa tu nombre completo" required />
        </div>

        <div class="form-group">
          <label for="fechaNacimiento">Fecha de nacimiento</label>
          <input v-model="formData.fechaNacimiento" type="date" id="fechaNacimiento" required />
        </div>

        <div class="form-group">
          <label for="direccion">Dirección</label>
          <input v-model="formData.direccion" type="text" id="direccion" placeholder="Ingresa tu dirección" required />
        </div>

        <div class="form-group">
          <label for="telefono">Número de teléfono</label>
          <input v-model="formData.telefono" type="tel" id="telefono" placeholder="Ingresa tu número de teléfono" required />
        </div>

        <div class="form-group">
          <label for="correo">Correo electrónico</label>
          <input v-model="formData.correo" type="email" id="correo" placeholder="Ingresa tu correo electrónico" required />
        </div>

        <div class="form-group">
          <label for="genero">Género</label>
          <select v-model="formData.genero" id="genero" required>
            <option value="" disabled>Selecciona tu género</option>
            <option value="Masculino">Masculino</option>
            <option value="Femenino">Femenino</option>
            <option value="Otro">Otro</option>
          </select>
        </div>

        <div class="form-group">
          <label for="estadoCivil">Estado civil</label>
          <select v-model="formData.estadoCivil" id="estadoCivil" required>
            <option value="" disabled>Selecciona tu estado civil</option>
            <option value="Soltero">Soltero</option>
            <option value="Casado">Casado</option>
            <option value="Divorciado">Divorciado</option>
            <option value="Viudo">Viudo</option>
          </select>
        </div>

        <button type="submit">Enviar</button>
      </form>
    </div>

    <div class="cards-container" v-if="submittedForms.length">
      <div v-for="(form, index) in submittedForms" :key="index" class="card">
        <h2>Datos ingresados {{ index + 1 }}</h2>
        <p><strong>Nombre completo:</strong> {{ form.nombre }}</p>
        <p><strong>Fecha de nacimiento:</strong> {{ form.fechaNacimiento }}</p>
        <p><strong>Dirección:</strong> {{ form.direccion }}</p>
        <p><strong>Número de teléfono:</strong> {{ form.telefono }}</p>
        <p><strong>Correo electrónico:</strong> {{ form.correo }}</p>
        <p><strong>Género:</strong> {{ form.genero }}</p>
        <p><strong>Estado civil:</strong> {{ form.estadoCivil }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        nombre: '',
        fechaNacimiento: '',
        direccion: '',
        telefono: '',
        correo: '',
        genero: '',
        estadoCivil: ''
      },
      submittedForms: [] 
    };
  },
  methods: {
    handleSubmit() {
      this.submittedForms.push({ ...this.formData });

      this.formData = {
        nombre: '',
        fechaNacimiento: '',
        direccion: '',
        telefono: '',
        correo: '',
        genero: '',
        estadoCivil: ''
      };
    }
  }
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body, html {
  height: 100%;
  font-family: 'Helvetica Neue', sans-serif;
  background-color: #f8f9fa;
}

.form-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  width: 100%;
}

.form-container {
  background-color: #fff;
  padding: 40px;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
  max-width: 500px;
  width: 100%;
  margin-bottom: 30px;
}

h1 {
  font-size: 1.8rem;
  text-align: center;
  color: #333;
  margin-bottom: 20px;
}

.form-group {
  margin-bottom: 15px;
}

label {
  font-size: 0.9rem;
  margin-bottom: 5px;
  display: block;
  color: #555;
}

input, select {
  width: 100%;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
}

input:focus, select:focus {
  border-color: #007bff;
  outline: none;
}

button {
  width: 100%;
  padding: 12px;
  font-size: 1rem;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #0056b3;
}

.cards-container {
  width: 100%;
  max-width: 500px;
}

.card {
  background: linear-gradient(135deg, #e2e8f0, #ffffff);
  padding: 20px;
  margin-bottom: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-10px);
  box-shadow: 0 6px 25px rgba(0, 0, 0, 0.15);
}

.card h2 {
  font-size: 1.5rem;
  margin-bottom: 15px;
  color: #333;
}

.card p {
  font-size: 1rem;
  color: #555;
  margin-bottom: 8px;
  line-height: 1.6;
}

.card p strong {
  color: #333;
}
</style>
