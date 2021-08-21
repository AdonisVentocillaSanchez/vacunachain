<template>
  <div class="register">
    <div id="formulario" class="container">
      <h1>{{ title }}</h1>
      <h2 class="mb-3">Paciente</h2>
      <div class="container row">
        <div class="mb-3 col-6">
          <label for="tipodoc" class="form-label">Tipo Documento</label>
          <select id="tipodoc" class="form-select" v-model="tipodoc">
            <option selected>Selecione</option>
            <option value="DNI">D.N.I</option>
            <option value="Carnet">Carnet de Extranjería</option>
          </select>
        </div>
        <div class="mb-3 col-6">
          <label for="nrodoc" class="form-label">Nro Documento</label>
          <input
            type="number"
            class="form-control"
            id="nrodoc"
            v-model="RegistroVacunas.NumeroDocumento"
          />
        </div>
        <div class="mb-3 col-6 col-md-4">
          <label for="firstname" class="form-label">Nombres</label>
          <input
            type="text"
            class="form-control"
            id="firstname"
            v-model="RegistroVacunas.Nombres"
          />
        </div>
        <div class="mb-3 col-6 col-md-4">
          <label for="lastname1" class="form-label">Apellido Paterno</label>
          <input
            type="text"
            class="form-control"
            id="lastname1"
            v-model="RegistroVacunas.ApellidoPaterno"
          />
        </div>
        <div class="mb-3 col-6 col-md-4">
          <label for="lastname2" class="form-label">Apellido Materno</label>
          <input
            type="text"
            class="form-control"
            id="lastname2"
            v-model="RegistroVacunas.ApellidoMaterno"
          />
        </div>
        <div class="mb-3 col-6 col-md-3">
          <label for="phone" class="form-label">Teléfono</label>
          <input
            type="number"
            class="form-control"
            id="phone"
            v-model="RegistroVacunas.Telefono"
          />
        </div>
        <div class="mb-3 col-6 col-md-3">
          <label for="VaccineBrand" class="form-label"
            >Marca de la Vacuna</label
          >
          <select
            id="VaccineBrand"
            class="form-select"
            v-model="RegistroVacunas.Dosis.MarcaVacuna"
          >
            <option selected>Selecione</option>
            <option value="Pfizer">Pfizer</option>
            <option value="AstraZeneca">AstraZeneca</option>
            <option value="Sinopharm">Sinopharm</option>
          </select>
        </div>
        <div class="mb-3 col-6 col-md-3">
          <label for="VaccinationSite" class="form-label"
            >Lugar de vacunación</label
          >
          <input
            type="text"
            class="form-control"
            id="VaccinationSite"
            v-model="RegistroVacunas.Dosis.LugarVacunacion"
          />
        </div>
        <div class="mb-3 col-6 col-md-3">
          <label for="datetime" class="form-label">Fecha de vacunación</label>
          <input
            type="date"
            class="form-control"
            id="datetime"
            v-model="RegistroVacunas.Dosis.FechaVacunacion"
          />
        </div>
      </div>
      <h2 class="mb-3">Doctora</h2>
      <div class="container row">
        <div class="mb-3 col-6">
          <label for="tipodoc_doc" class="form-label">Tipo Documento</label>
          <select id="tipodoc_doc" class="form-select" v-model="tipodoc_doc">
            <option selected>Selecione</option>
            <option value="DNI">D.N.I</option>
            <option value="Carnet">Carnet de Extranjería</option>
          </select>
        </div>
        <div class="mb-3 col-6">
          <label for="nrodoc_doc" class="form-label">Nro Documento</label>
          <input
            type="text"
            class="form-control"
            id="nrodoc_doc"
            v-model="RegistroVacunas.Dosis.Tecnica.NumeroDocumento"
          />
        </div>
        <div class="mb-3 col-6 col-md-4">
          <label for="firstname_doc" class="form-label">Nombres</label>
          <input
            type="text"
            class="form-control"
            id="firstname_doc"
            v-model="RegistroVacunas.Dosis.Tecnica.Nombres"
          />
        </div>
        <div class="mb-3 col-6 col-md-4">
          <label for="lastname1_doc" class="form-label">Apellido Paterno</label>
          <input
            type="text"
            class="form-control"
            id="lastname1_doc"
            v-model="RegistroVacunas.Dosis.Tecnica.ApellidoPaterno"
          />
        </div>
        <div class="mb-3 col-6 col-md-4">
          <label for="lastname2_doc" class="form-label">Apellido Materno</label>
          <input
            type="text"
            class="form-control"
            id="lastname2_doc"
            v-model="RegistroVacunas.Dosis.Tecnica.ApellidoMaterno"
          />
        </div>
      </div>
      <div class="row justify-content-center">
        <button class="btn btn-primary col-3" @click="addPaciente">
          Submit
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "RegisterVaccine",
  props: {
    title: String
  },
  data() {
    return {
      tipodoc:'',
      tipodoc_doc:'',
      // desde aca
      registro:[],
      bodyData:[],
      RegistroVacunas: {
        FechaNacimiento: "",
        Nombres: "",
        ApellidoPaterno: "",
        ApellidoMaterno: "",
        NumeroDocumento: "",
        Telefono: "",
        Dosis: {
          numeroDosis: 1,
          LugarVacunacion: "",
          MarcaVacuna: "",
          FechaVacunacion: "",
          Tecnica: {
            Nombres: "",
            ApellidoPaterno: "",
            ApellidoMaterno: "",
            NumeroDocumento: ""
          }
        }
      }
    };
  },
  methods: {
    addPaciente: function() {
      this.registro = {
        RegistroVacunas: {
        FechaNacimiento: this.RegistroVacunas.FechaNacimiento,
        Nombres: this.RegistroVacunas.Nombres,
        ApellidoPaterno: this.RegistroVacunas.ApellidoPaterno,
        ApellidoMaterno: this.RegistroVacunas.ApellidoMaterno,
        NumeroDocumento: this.RegistroVacunas.NumeroDocumento,
        Telefono: this.RegistroVacunas.Telefono,
        Dosis: {
          numeroDosis: 1,
          LugarVacunacion: this.RegistroVacunas.Dosis.LugarVacunacion,
          MarcaVacuna: this.RegistroVacunas.Dosis.MarcaVacuna,
          FechaVacunacion: this.RegistroVacunas.Dosis.FechaVacunacion,
          Tecnica: {
            Nombres: this.RegistroVacunas.Tecnica.Nombres,
            ApellidoPaterno: this.RegistroVacunas.Tecnica.ApellidoPaterno,
            ApellidoMaterno: this.RegistroVacunas.Tecnica.ApellidoMaterno,
            NumeroDocumento: this.RegistroVacunas.Tecnica.NumeroDocumento
          }
        }
      }
      };
      console.log(this.registro);
      this.bodyData = {
        name:"RegisterTest",
        comentario:this.registro,
        primeraDosis:{
          NumeroDocumento: this.RegistroVacunas.NumeroDocumento
        }
      }
      console.log(this.RegistroVacunas.NumeroDocumento);
      const URLpostData = "https://hack-unmsm.herokuapp.com/api/v1/data-blockchain";
      axios.post(URLpostData, this.bodydata)
      .then(data => {
        console.log(data);
      })
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
