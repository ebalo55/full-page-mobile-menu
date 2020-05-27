<template>
    <div id="app">
        <div class="menu-toggle" @click="isMenuOpen = true">
            <span class="fas fa-bars"></span>
        </div>
        <img class="background-img" src="/assets/background.jpg">
        <div :class="menu_class" :style="menu_transition">
            <div class="menu-toggle-internal" @click="isMenuOpen = false"
                :style="toggle_internal_transition">
                <span class="fas fa-times"></span>
            </div>
            <ul>
                <li v-for="(item, index) of urls" :key="index">
                    <a :href="item.href" v-html="item.label"></a>
                    <hr>
                </li>
            </ul>
            <ul class="socials">
                <li v-for="(item, index) of socials" :key="index">
                    <a :href="item.href" v-html="item.label"></a>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'App',
    data: function() {
        return {
            isMenuOpen: false,
            urls: [
                {href: "#", label: `<span class="fas fa-home"></span> Home`},
                {href: "#", label: `<span class="fas fa-box"></span> Orders`},
                {href: "#", label: `<span class="fas fa-truck"></span> Delivery`},
                {href: "#", label: `<span class="fas fa-user-shield"></span> Privacy`},
                {href: "#", label: `<span class="fas fa-cog"></span> Settings`},
                {href: "#", label: `<span class="far fa-question-circle"></span> FAQ`},
            ],
            socials: [
                {href: "#", label: `<span class="fab fa-facebook"></span>`},
                {href: "#", label: `<span class="fab fa-twitter"></span>`},
                {href: "#", label: `<span class="fab fa-instagram"></span>`},
                {href: "#", label: `<span class="fab fa-linkedin"></span>`},
            ]
        };
    },
    computed: {
        menu_class: function() {
            return `menu-wrapper ${this.isMenuOpen ? "show" : ""}`;
        },
        menu_transition: function() {
            return !this.isMenuOpen ? "transition-delay: .5s;" : "";
        },
        toggle_internal_transition: function() {
            return this.isMenuOpen ? "transition-delay: .5s;" : "";
        }
    }
}
</script>
