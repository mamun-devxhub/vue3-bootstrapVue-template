<template>
  <BForm
    @submit="onSubmit"
    @reset="onReset"
    v-if="show"
    novalidate
    class="needs-validation"
    :validated="false"
  >
    <BFormGroup
      id="input-group-1"
      label="Email address:"
      label-for="input-1"
      description="We'll never share your email with anyone else."
    >
      <BFormInput
        id="input-1"
        v-model="form.email"
        type="email"
        placeholder="Enter email"
        required
        aria-describedby="password-help-block"
      />
      <BFormText id="password-help-block">
        Your password must be 8-20 characters long, contain letters and numbers, and must not
        contain spaces, special characters, or emoji.
      </BFormText>
      <BFormInvalidFeedback :state="validation">
        Your user Id must be 5-12 characters long.
      </BFormInvalidFeedback>
      <BFormValidFeedback :state="validation"> Looks Good. </BFormValidFeedback>
    </BFormGroup>

    <BFormGroup id="input-group-2" label="Your Name:" label-for="input-2">
      <BFormInput id="input-2" v-model="form.name" placeholder="Enter name" required />
    </BFormGroup>
    <BFormGroup id="input-group-3" label="Food:" label-for="input-3">
      <BFormSelect id="input-3" v-model="form.food" :options="foods" required />
    </BFormGroup>

    <BFormGroup id="input-group-4">
      <BFormCheckboxGroup v-model="form.checked" id="checkboxes-4">
        <BFormCheckbox value="me">Check me out</BFormCheckbox>
        <BFormCheckbox value="that">Check that out</BFormCheckbox>
      </BFormCheckboxGroup>
    </BFormGroup>
    <BButton type="submit" variant="primary">Submit</BButton>
    <BButton type="reset" variant="danger">Reset</BButton>
  </BForm>

  <BCard class="mt-3" header="Form Data Result">
    <pre class="m-0">{{ form }}</pre>
  </BCard>
</template>

<script setup lang="ts">
import { nextTick, reactive, ref, computed } from 'vue'
import { useToast } from 'vue-toastification'
const toast = useToast()

const foods = [{ text: 'Select One', value: null }, 'Carrots', 'Beans', 'Tomatoes', 'Corn']

const validation = computed(() => form.email.length > 4 && form.email.length < 13)

const form = reactive({
  email: '',
  name: '',
  food: null,
  checked: []
})
const show = ref(true)

const onSubmit = (event: { preventDefault: () => void }) => {
  console.log(event, 'event')
  if (!validation.value) {
    toast.error('Your user Id must be 5-12 characters long.')
    return
  }

  event.preventDefault()
  alert(JSON.stringify(form))
}

const onReset = (event: { preventDefault: () => void }) => {
  event.preventDefault()
  // Reset our form values
  form.email = ''
  form.name = ''
  form.food = null
  form.checked = []
  // Trick to reset/clear native browser form validation state
  show.value = false
  nextTick(() => {
    show.value = true
  })
}
</script>
