<template>
    <section>
        <!-- Add click event listener -->
        <button @click="change_layout">Change layout</button>
        <div ref="posts_container">
            <!-- Loop over the tweets array to display all tweets -->
            <article v-for="(tweet,i) in tweets" :key="i" class="post_card">
                <h3>{{tweet[`user`]}}</h3>
                <p>{{tweet[`date`]}}</p>
                <p>{{tweet[`content`]}}</p>
            </article>
        </div>
    </section>
</template>

<script>
    export default {
        data() {
            return {
                 tweets: [
                    {
                        content: `Just finished a 10K run and feeling great! It's amazing what you can accomplish when you set your mind to it 🏃‍♂️ #fitnessmotivation #nevergiveup`,
                        user: `@johndoe`,
                        date: `April 15, 2023`
                    },
                    {
                        content: `I can't believe it's already Friday! Time flies when you're having fun 😎 #TGIF #weekendvibes`,
                        user: `@sarahj`,
                        date: `April 15, 2023`
                    },
                    {
                        content: `Excited to announce that I'll be speaking at the upcoming Tech Summit on May 1st! Can't wait to share my insights on the latest trends in #AI and #machinelearning 🤖`,
                        user: `@davidlee`,
                        date: `April 15, 2023`
                    }
                ] 
            }
        },
        methods: {
            change_layout: function() 
            {
                //Toggle the layout direction by comparing the grid-auto-flow css property and changing it accordingly.
                if(this.$refs[`posts_container`][`style`][`gridAutoFlow`] !== `column`)
                {
                    this.$refs[`posts_container`][`style`][`gridAutoFlow`] = `column`;
                }
                else
                {
                    this.$refs[`posts_container`][`style`][`gridAutoFlow`] = `row`;
                }
            }
        }
    }
</script>
<style scoped>
    div {
        display:grid;
    }
</style>