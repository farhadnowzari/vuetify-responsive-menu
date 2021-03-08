<template>
    <v-menu v-bind="menuAttrs"
            v-if="!switchBreakpoint"
            v-model="visible">
        <template
                  v-slot:activator="{ on, attrs }">
            <span @click="visible  = true">
                <slot @click="visible  = true"
                    name="activator"
                    v-on="on"
                    v-bind="attrs"></slot>
            </span>
        </template>
        <slot></slot>
    </v-menu>
    <v-dialog v-bind="dialogAttrs"
              v-else
              v-model="visible">
        <template
                  v-slot:activator="{ on, attrs }">
            <span @click="visible = true">
                            <slot name="activator"
                  v-on="on"
                  v-bind="attrs"></slot>
            </span>
        </template>
        <slot></slot>
    </v-dialog>
</template>

<script>
import { VDialog, VMenu } from "vuetify/lib";

export default {
    components: {
        VDialog,
        VMenu,
    },
    computed: {
        dialogAttrs() {
            const filtered = Object.keys(this.$attrs)
                .filter((key) => key.startsWith("dialog-"))
                .reduce((obj, key) => {
                    obj[key.replace("dialog-", "")] = this.$attrs[key];
                    return obj;
                }, {});
            return filtered;
        },
        menuAttrs() {
            const filtered = Object.keys(this.$attrs)
                .filter((key) => key.startsWith("menu-"))
                .reduce((obj, key) => {
                    obj[key.replace("menu-", "")] = this.$attrs[key];
                    return obj;
                }, {});
            return filtered;
        },
    },
    methods: {
        close() {
            this.visible = false;
        },
        open() {
            this.visible = true;
        },
        save() {
            this.$emit("update:returnValue", this.returnValue);
            this.visible = false;
        },
    },
    data() {
        return {
            visible: false,
        };
    },
    name: "v-responsive-menu",
    props: {
        returnValue: {},
        switchBreakpoint: Boolean,
    },
};
</script>