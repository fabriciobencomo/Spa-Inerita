<template>
    <app-layout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Notes
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="md:grid md:grid-cols-3 md:gap-6">
                    <div class="md:col-span-1">
                        <div class="px-4 sm:px-0">
                            <h3 class="text-lg text-gray-900">Create Note</h3>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <form @submit.prevent="submit">
                                <label class="block font-medium text-sm text-gray-700">Description:</label>
                                <textarea class="form-input w-full rounded-md shadow-sm" v-model="form.excerpt"></textarea>

                                <label class="block font-medium text-sm text-gray-700">Content:</label>
                                <textarea class="form-input w-full rounded-md shadow-sm" v-model="form.content" rows="8"></textarea>

                                <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold px-4 py-2 rounded-md mt-3">Save</button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </app-layout>
</template>

<script>
    import { defineComponent } from 'vue'
    import AppLayout from '@/Layouts/AppLayout.vue'
    import Welcome from '@/Jetstream/Welcome.vue'
    import { Link } from '@inertiajs/inertia-vue3'

    export default defineComponent({
        components: {
            AppLayout,
            Link
        },
        data (){
            return  {
                form: {
                    excerpt: '',
                    content: ''
                }
            }
        },
        methods: {
            submit()
            {
                this.$inertia.post(this.route('notes.store'), this.form)
            }
        }
    })
</script>
