<script setup>
const props = defineProps(['number1', 'escolheOperacao', 'number2'])
</script>

<template>
    <form>
        <div class="row">
            <div class="col">
                <input @keyup="props.number1" type="number" class="form-control"
                    placeholder="0">
            </div>

            <div class="col">
                <select @change="props.escolheOperacao" class="form-control">
                    <option value="soma">Soma</option>
                    <option value="subtracao">Subtração</option>
                    <option value="divisao">Divisão</option>
                    <option value="multiplicao">Multiplição</option>
                </select>
            </div>

            <div class="col">
                <input @keyup="props.number2" type="number" class="form-control"
                    placeholder="0">
            </div>
        </div>
    </form>
</template>