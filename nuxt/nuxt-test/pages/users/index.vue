<template>
    <div class="content">
        <div
            class="user__wrapper"
            v-for="(item, index) in usersStore.users"
            :key="index"
            @click="goToUser(item.id)"
        >
            <p>
                {{ item.name }}
            </p>
        </div>
    </div>
</template>

<script setup lang="ts">
    useHead({
        title: `Users`
    })

    const usersStore = useUsersStore()
    usersStore.getUsers()
    
    const goToUser = (id: number) => navigateTo(`/users/${id}`)
</script>

<style lang="scss" scoped>
.content{
    height: 100vh;
    padding: 20px 0;
    display: flex;
    flex-direction: column;
    gap: 15px;
    align-items: center;
    justify-content: space-between;
}
.user__wrapper{
    width: 70%;
    height: 50px;
    background: $df-color-dark;
    border-radius: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    p{
        color: $tx-color-white;
        font-size: 25px;
        font-style: italic;
        font-weight: 600;
    }

    &:hover{
        cursor: pointer;
    }
}
</style>