<template>
    <header class="p-3 bg-sec">
        <div
            class="container"
        >
            <div class="row">
                <div class="col-12 col-md-6">
                    <div class="brand">
                        <img
                            src="https://fontmeme.com/permalink/211201/23ce322a0021620e5e3988113b05d104.png"
                            alt=""
                        />
                    </div>
                </div>

                <div class="col-12 col-md-6 d-flex justify-content-end align-items-center text-right">
                    <div class="cta d-flex align-items-center">
                        <input
                            type="text"
                            class="bg-prim"
                            v-model.trim="userQuery"
                            @keyup.enter="$emit('search', userQuery)"
                        />

                        <button
                            class="bg-prim text-light py-2 px-4 mx-2 border-0"
                            @click="$emit('search', userQuery)"
                        >
                            Search
                        </button>
                    </div>

                </div>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            userQuery: "",
        };
    },
};
</script>

<style lang="scss" scoped>
.brand {
    img {
        width: 300px;
    }
}

.cta {
    color: white;
    input {
        outline: none;
        color: white;
    }
    button:hover {
        background: #222222;
    }
}
</style>
