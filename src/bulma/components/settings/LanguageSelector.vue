<template>
    <core-language-selector>
        <template v-slot:default="{ languages, locale, update }">
            <div class="level is-mobile">
                <div class="level-left">
                    <div class="level-item">
                        {{ i18n('Language') }}
                    </div>
                </div>
                <div class="level-right">
                    <div class="level-item language-selector">
                        <dropdown>
                            <template v-slot:label>
                                <span class="icon">
                                    <i :class="languages[locale]"/>
                                </span>
                            </template>
                            <template v-slot:options>
                                <a v-for="(flag, lang) in languages"
                                    :key="lang"
                                    class="dropdown-item has-text-centered"
                                    :class="{ 'is-active': flag === languages[locale] }"
                                    @click="update(lang)">
                                    <span class="icon is-small">
                                        <i :class="flag"/>
                                    </span>
                                </a>
                            </template>
                        </dropdown>
                    </div>
                </div>
            </div>
        </template>
    </core-language-selector>
</template>

<script>
import { Dropdown } from '@enso-ui/bulma';
import CoreLanguageSelector from '../../../core/components/settings/LanguageSelector.vue';

export default {
    name: 'LanguageSelector',

    components: { CoreLanguageSelector, Dropdown },

    inject: ['i18n'],
};
</script>

<style lang="scss">
    @import './flags/flags';

    .language-selector {
        .button .icon:first-child:not(:last-child) {
            margin: unset;
        }

        .dropdown .dropdown-content {
            width: 4.6em;
            .options {
                width: 4.6em;
            }
        }
    }
</style>
