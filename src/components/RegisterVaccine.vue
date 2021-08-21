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
      // data paciente
      tipodoc: "",
      nrodoc: "",
      firstname: "",
      lastname1: "",
      lastname2: "",
      phone: "",
      // data vacuna
      VaccineBrand: "",
      VaccinationSite: "",
      datetime: "",
      dosis: 1,
      // data doc
      tipodoc_doc: "",
      nrodoc_doc: "",
      firstname_doc: "",
      lastname1_doc: "",
      lastname2_doc: "",
      // desde aca
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
      console.log("click p mano");
      this.getDataDNI(this.nrodoc);
    },
    getDataDNI(dni) {
      console.log(dni);
      const URLgetDNI = "https://dni.optimizeperu.com/api/prod/persons/";
      const TOKEN = "k4d2956bd531ab61d44f4fa07304b20e13913815";
      axios
        .create({
          baseURL: URLgetDNI,
          headers: {
            "Content-Type": "application/json",
            Authorization: "token " + TOKEN
          }
        })
        .get(dni)
        .then(res => {
          console.log(res);
        });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
