<template>
  <div class="main">
    <FacultyNavBar />
    <div class="container">
      <div class="py-5 text-center">
        <img
          class="d-block mx-auto mb-4"
          src="/docs/4.3/assets/brand/bootstrap-solid.svg"
          alt
          width="72"
          height="72"
        />
        <h2>Add a Notice</h2>
        <p class="lead">Enter details about notes that students need to know</p>
      </div>

      <div class="row">
        <div class="col-md-3"></div>
        <div class="col-md-6 order-md-1">
          <h4 class="mb-3">Notice Details</h4>
          <form class="needs-validation" novalidate>
            <div class="mb-3">
              <label for="Location">Notice Title</label>
              <div class="input-group">
                <input
                  type="text"
                  class="form-control"
                  id="location"
                  placeholder="Title"
                  required
                  v-model="noteData.title"
                />
                <div class="invalid-feedback" style="width: 100%;">Title is required.</div>
              </div>
            </div>
            <div class="mb-3">
              <label for="Location">Notice Sub Title</label>
              <div class="input-group">
                <input
                  type="text"
                  class="form-control"
                  id="location"
                  placeholder="Subtitle"
                  required
                  v-model="noteData.subtitle"
                />
              </div>
            </div>

            <h4 class="mb-3">Description</h4>
            <div class="md-3">
              <textarea
                placeholder="Enter Notice"
                rows="20"
                name="comment[text]"
                id="comment_text"
                cols="40"
                class="ui-autocomplete-input"
                autocomplete="off"
                role="textbox"
                aria-autocomplete="list"
                aria-haspopup="true"
                v-model="noteData.description"
              ></textarea>
            </div>
            <div class="row">
              <div class="col-md-4 mb-3">
                <label for="country">Batch</label>
                <select
                  class="custom-select d-block w-100"
                  id="country"
                  required
                  v-model="selectedBatch"
                >
                  <option v-for="batch in batches">{{ batch }}</option>
                </select>
                <div class="invalid-feedback">Please select any of choice</div>
              </div>
              <div class="col-md-4 mb-3">
                <label for="state">Faculty</label>
                <select
                  class="custom-select d-block w-100"
                  id="state"
                  required
                  v-model="selectedFaculty"
                >
                  <option
                    v-for="faculty in faculties"
                    v-bind:value="faculty.id"
                    :selected="selectedFaculty==0"
                  >{{ faculty.name }}</option>
                </select>
                <div class="invalid-feedback">Please select one of them</div>
              </div>
              <div class="col-md-4 mb-3">
                <label for="state">Degree</label>
                <select
                  class="custom-select d-block w-100"
                  id="state"
                  required
                  v-model="selectedDegree"
                >
                  <option v-for="degree in degrees">{{ degree }}</option>
                </select>
                <div class="invalid-feedback">Please select one of them</div>
              </div>
            </div>
            <hr class="mb-4" />
            <button
              class="btn btn-primary btn-lg btn-block"
              type="button"
              v-on:click="submitted()"
            >Publish Notice</button>
          </form>
        </div>
      </div>
      <footer class="my-5 pt-5 text-muted text-center text-small"></footer>
    </div>
    <Footer />
  </div>
</template>

<script>
import FacultyNavBar from "./FacultyNavbar";
import Footer from "../Footer";
import axios from "axios";
export default {
  name: "NoticeAdd",
  components: { Footer, FacultyNavBar },
  data() {
    return {
      noteData: {
        title: "",
        subtitle: "",
        description: ""
      },
      selectedBatch: "All...",
      selectedFaculty: 0,
      selectedDegree: "All...",
      batches: [
        "All...",
        "17.1",
        "17.2",
        "18.1",
        "18.2",
        "19.1",
        "19.2",
        "20.1"
      ],
      faculties: [
        { id: 0, name: "All..." },
        { id: 1, name: "Computing" },
        { id: 2, name: "Bussiness" },
        { id: 3, name: "Engineering" }
      ],
      degrees: ["All...", "Plymouth SE", "Dublin MSI", "UGC CS"],
      isSubmitted: false
    };
  },
  // mounted() {
  //     axios
  //     .get('http://192.168.43.199:8083/api/notes/notes')
  //     console.log('Component mounted.')

  // },
  methods: {
    submitted() {
      if (
        this.noteData.title != "" &&
        this.noteData.subtitle != "" &&
        this.noteData.description != ""
      ) {
        this.isSubmitted = true;
        this.$router.replace({ name: "NoticeAdd" });
        axios
          .post("http://192.168.43.199:8083/api/notes/notes", {
            title: this.noteData.title,
            subtitle: this.noteData.subtitle,
            description: this.noteData.description,
            batch: this.selectedBatch,
            faculty: {
              id: this.selectedFaculty
            },
            degree: this.selectedDegree

            //         this.selectedBatch);
            // console.log(this.selectedFaculty);
            // console.log(this.selectedDegree
            //     })
            //     .then(res => {
          })
          .then(res => {
            // this.noteData = undefined;
            // selectedBatch = "All...";
            // selectedFaculty = 0;
            // selectedDegree = "All...";
          });
        // axios
        //     .post('http://192.168.43.199:8083/api/notes/notes',{
        //                 title: 'hello',
        //                 subtitle: 'hello',
        //                 description: 'hello',
        //                 batch: 'hello',
        //                 degree: 'hello',
        //                 faculty: 'hello',

        //         })
        console.log(this.noteData.title);
        console.log(this.noteData.subtitle);
        console.log(this.noteData.description);
        console.log(this.selectedBatch);
        console.log(this.selectedFaculty);
        console.log(this.selectedDegree);
      }
    }
  }
};
</script>

<style scoped>
.main {
  margin-top: -60px;
}

.topbar-responsive {
  background-color: #19589d;
  padding: 1rem 1.5rem;
}

.topbar-responsive .topbar-responsive-logo {
  color: #fefefe;
  vertical-align: middle;
}

.topbar-responsive .menu {
  background-color: #19589d;
}

.topbar-responsive .menu li:last-of-type {
  margin-right: 0;
}

.topbar-responsive .menu a {
  color: #fefefe;
  transition: color 0.15s ease-in;
}

.topbar-responsive .menu a:hover {
  color: #c6d1d8;
}

@media screen and (max-width: 39.9375em) {
  .topbar-responsive .menu a {
    padding: 0.875rem 0;
  }
}

.topbar-responsive .menu .topbar-responsive-button {
  color: #fefefe;
  border-color: #fefefe;
  border-radius: 5000px;
  transition: color 0.15s ease-in, border-color 0.15s ease-in;
}

.topbar-responsive .menu .topbar-responsive-button:hover {
  color: #c6d1d8;
  border-color: #c6d1d8;
}

@media screen and (max-width: 39.9375em) {
  .topbar-responsive .menu .topbar-responsive-button {
    width: 100%;
    margin: 0.875rem 0;
  }
}

@media screen and (max-width: 39.9375em) {
  .topbar-responsive {
    padding: 0.75rem;
  }
  .topbar-responsive .top-bar-title {
    position: relative;
    width: 100%;
  }
  .topbar-responsive .top-bar-title span {
    position: absolute;
    right: 0;
    border: 1px solid #fefefe;
    border-radius: 5px;
    padding: 0.25rem 0.45rem;
    top: 50%;
    -webkit-transform: translateY(-50%);
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }
  .topbar-responsive .top-bar-title span .menu-icon {
    margin-bottom: 4px;
  }
}

@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@-webkit-keyframes slideDown {
  0% {
    -webkit-transform: translateY(-100%);
    transform: translateY(-100%);
  }
  100% {
    -webkit-transform: translateY(0%);
    transform: translateY(0%);
  }
}

@keyframes slideDown {
  0% {
    -webkit-transform: translateY(-100%);
    transform: translateY(-100%);
  }
  100% {
    -webkit-transform: translateY(0%);
    transform: translateY(0%);
  }
}

@media screen and (max-width: 39.9375em) {
  .topbar-responsive-links {
    -webkit-animation-fill-mode: both;
    animation-fill-mode: both;
    -webkit-animation-duration: 0.5s;
    animation-duration: 0.5s;
    width: 100%;
    -webkit-animation: fadeIn 1s ease-in;
    animation: fadeIn 1s ease-in;
  }
}
b {
  color: #fefefe;
  margin-left: 20px;
  font-family: "Proxima Nova", "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 24px;
}
.active {
  font-weight: bolder;
  text-decoration: none;
}
</style>