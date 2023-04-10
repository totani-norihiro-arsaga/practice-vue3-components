<script setup>
</script>
<template>
    <div>
        <slot name="title" message="ユーザーslot props"></slot>
    </div>
    <div>
        <slot name="contents" message="コンテンツslot props"></slot>
    </div>
    <div>
        <slot name="action">アクション</slot>
    </div>
    <div>
        <slot>名前なし</slot>
    </div>
</template>