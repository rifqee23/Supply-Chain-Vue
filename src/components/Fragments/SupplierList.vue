<script setup>
import { ref } from "vue";
import Button from "../Elements/Button.vue";
import SupplierForm from "./SupplierForm.vue";

const users = ref([
  {
    id: 1,
    username: "Asep",
    email: "asep@gmail.com",
    role: "supplier",
  },
]);

const formPage = ref("list");
const selectedUser = ref(null);

const handleEdit = (user) => {
  selectedUser.value = { ...user }; // Salin data user yang akan diedit
  formPage.value = "edit";
};

const handleAdd = () => {
  selectedUser.value = null; // Reset selected user saat add
  formPage.value = "add";
};

const backToList = () => {
  formPage.value = "list";
  selectedUser.value = null; // Reset selected user saat kembali
};

const handleSubmit = (formData) => {
  if (formPage.value === "edit" && selectedUser.value) {
    const index = users.value.findIndex((u) => u.id === selectedUser.value.id);
    if (index !== -1) {
      users.value[index] = {
        ...users.value[index],
        ...formData,
      };
    }
  } else {
    const newUser = {
      id: users.value.length + 1,
      ...formData,
    };
    users.value.push(newUser);
  }
  formPage.value = "list";
  selectedUser.value = null;
};

const deleteUser = (userId) => {
  if (confirm("Are you sure want to delete this user?")) {
    users.value = users.value.filter((user) => user.id !== userId);
  }
};
</script>

<template>
  <div v-if="formPage === 'add'">
    <SupplierForm @back="backToList" @submit="handleSubmit" :isEdit="false" />
  </div>

  <div v-if="formPage === 'edit'">
    <SupplierForm
      @back="backToList"
      @submit="handleSubmit"
      :user="selectedUser"
      :isEdit="true"
    />
  </div>

  <div v-if="formPage === 'list'">
    <div class="flex justify-between px-4 mt-2">
      <div>Supplier List</div>
      <Button
        class="bg-green-500 text-white px-4 py-1 rounded-lg"
        @click="handleAdd"
      >
        Add
      </Button>
    </div>
    <div class="overflow-x-auto">
      <table class="w-full">
        <thead>
          <tr>
            <th class="border-b-2 px-4">No</th>
            <th class="border-b-2 px-4">Username</th>
            <th class="border-b-2 px-4">Email</th>
            <th class="border-b-2 px-4">Role</th>
            <th class="border-b-2 px-4">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(user, index) in users" :key="user.id">
            <td class="border-b text-center">{{ index + 1 }}</td>
            <td class="border-b text-center">{{ user.username }}</td>
            <td class="border-b text-center">{{ user.email }}</td>
            <td class="border-b text-center">{{ user.role }}</td>
            <td class="border-b text-center flex flex-col gap-y-2 my-2">
              <Button class="bg-blue-500 text-white" @click="handleEdit(user)">
                Edit
              </Button>
              <Button
                class="bg-red-500 text-white"
                @click="deleteUser(user.id)"
              >
                Delete
              </Button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
