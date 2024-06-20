<script setup>
import algoliasearch from 'algoliasearch/lite';
import { usePage } from '@inertiajs/vue3';
const page = usePage();
const algolia = page.props.algolia;
const searchClient = algoliasearch(
    algolia.key,
    ...algolia.searchables
);
</script>

<template>
  <section >
        <ais-instant-search
            :search-client="searchClient"
            index-name="products"
        >
            <ais-configure
                :hits-per-page.camel="4"
            />

            <ais-search-box
                placeholder="text"
            />
            <div>
                <ais-hits>
                    <template v-slot:item="{ item }">
                        <article>
                            {{ item.title }}
                        </article>
                    </template>
                </ais-hits>
            </div>
        </ais-instant-search>
    </section>
</template>
