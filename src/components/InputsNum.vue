<template>
    <div>
        <label class="block font-medium px-9">{{ label }}</label>
        <input v-bind="value" :type="type" :min="min" :max="max" class="form-input mt-1 block w-full">
    </div>
</template>

<script>
    export default {
        props: {
            label: {
                type: String,
                required: true,
            },
            type: {
                type: String,
                default: 'number',
            },
            value: {
                type: [String, Number],
                required: true,
            },
            min: {
                type: String,
                default: 18,
            },
            max: {
                type: String,
                default: 99,
            }
        },
    };
</script>