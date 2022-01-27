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
                            <h3 class="text-lg text-gray-900">Note-List</h3>
                            <p class="text-sm text-gray-600">Take a Register and Excute any Function (Read, Edit or Delete)</p>
                            <Link :href="route('notes.create')"><button class="bg-blue-500 hover:bg-blue-700 text-white font-bold px-4 py-2 rounded-md mt-3">Create</button></Link>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <table>
                                <tr v-for="note in notes">
                                    <td class="border px-4 py-2">
                                        {{note.excerpt}}
                                    </td>
                                    <td class="px-4 py-2">
                                        <Link :href="route('notes.show', note.id)">Read More</Link>
                                    </td>
                                    <td class="px-4 py-2">
                                        <Link :href="route('notes.edit', note.id)">Edit</Link>
                                    </td>
                                    <td class="px-4 py-2">
                                        <a href="#" @click.prevent="destroy(note.id)">Delete </a>
                                    </td>
                                </tr>
                            </table>
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
    import { Head, Link } from '@inertiajs/inertia-vue3'

    export default defineComponent({
        components: {
            AppLayout,
            Link
        },
        props: {
            notes: Array,
        },
        methods: {
            destroy($id)
            {
                if(confirm("This Action is Irreversible. Are You Sure?")){
                    this.$inertia.delete(this.route('notes.destroy', $id ))
                }

            }
        }
    })
</script>
