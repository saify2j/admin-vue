<template>
  <div class="container">
    <script type="text/x-template" id="modal-template">
      <transition name="modal">
        <div class="modal-mask">
          <div class="modal-wrapper">
            <div class="modal-container">

              <div class="modal-header">
                <slot name="header">
                  default header
                </slot>
              </div>

              <div class="modal-body">
                <slot name="body">
                  default body
                </slot>
              </div>

              <div class="modal-footer">
                <slot name="footer">
                  default footer
                  <button class="modal-default-button" @click="$emit('close')">
                    OK
                  </button>
                </slot>
              </div>
            </div>
          </div>
        </div>
      </transition>
    </script>
    <div class="col-lg-6">
      <div class="card">
        <div class="card-header">
          <h3 class="card-title">Collapsible Card Example</h3>
          <div class="card-tools">
            <!-- Collapse Button -->
            <button type="button" id="toggleB" @click="toggleComponentOne" class="btn btn-tool">
              <i class="fas fa-plus"></i>
            </button>
          </div>
          <!-- /.card-tools -->
        </div>
        <!-- /.card-header -->
        <Card v-if="showComponentOne" />
        <!-- /.card-body -->
      </div>
    </div>
    <div class="col-lg-6">
      <button id="show-modal" @click="showModal = true" class="btn btn-success">Add new</button>
      <!-- use the modal component, pass in the prop -->
      <modal v-if="showModal" @close="showModal = false"></modal>
    </div>
    <div class="col-lg-6">
      <!-- Button trigger modal -->
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">
  Launch demo modal
</button>

<!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        ...
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>
    </div>
  </div>
</template>

<script>
Vue.component("modal", {
        template: "#modal-template"
      });
import Card from "./Card";
export default {
  name: "App",
  components: {
    Card
  },
  data() {
    return {
      showComponentOne: false,
      showModal: false
    };
  },
  methods: {
    toggleComponentOne() {
      var button = document.getElementById("toggleB");
      if (this.showComponentOne === true) {
        button.innerHTML = `
        <i class="fas fa-minus"></i>
        `;
      } else {
        button.innerHTML = `
        <i class="fas fa-plus"></i>
        `;
      }

      this.showComponentOne = !this.showComponentOne;
    },
  }
};
</script>
