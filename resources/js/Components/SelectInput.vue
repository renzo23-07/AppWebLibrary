<template>
    <label class="block text-sm">
            <!-- focus-within sets the color for the icon when input is focused -->
        <div class="relative text-gray-500 focus-within:text-purple-600 dark:focus-within:text-purple-400">
            <select class="rounded block w-full pl-10 mt-1 text-sm text-black dark:text-gray-900 dark:border-gray-600 dark:bg-gray-50 focus:border-purple-400 focus:outline-none focus:shadow-outline-purple dark:focus:shadow-outline-gray form-input" 
            :value="modelValue" @input="$emit('update:modelValue', $event.target.value)" ref="input" 
            :placeholder="text"  :required="required">
            
            <option value="" selected>{{ text }}</option>
            <option v-for="op in options" :key="op.id" :value="op.id">
                {{ op.country }}
            </option>
            </select>
            <div class="absolute inset-y-0 flex items-center ml-3 pointer-events-none">
                <slot>
                    
                </slot>
            </div>
        </div>
    </label>
  </template>
  
  <script setup>
  import { onMounted, ref } from 'vue';
  
  defineProps(['modelValue','text','options','required']);
  
  defineEmits(['update:modelValue']);
  
  const input = ref(null);
  
  onMounted(() => {
      if (input.value.hasAttribute('autofocus')) {
          input.value.focus();
      }
  });
  </script>