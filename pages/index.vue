<template>
  <div>
    <div class="px-6 py-12 lg:py-32 bg-blue-400 text-white">
      <div class="container mx-auto">
        <div
          class="grid gap-12 lg:grid-cols-2 lg:gap-24 w-full lg:items-center"
        >
          <div>
            <responsive-screens class="w-full" />
          </div>
          <div>
            <h1 class="text-3xl lg:text-5xl font-bold leading-tight mb-4">
              Professional Web Design & Web Development
            </h1>
            <p class="text-lg lg:text-2xl">
              With over 40 years of combined experience in the digital
              marketplace,
              <strong>moejoe</strong> can offer what you are looking for, from a
              landing page to a complex multipage web application.
            </p>
          </div>
        </div>
      </div>
    </div>
    <div class="px-6 py-12 lg:py-24 bg-gray-100">
      <div class="container mx-auto">
        <div class="grid gap-12 lg:gap-24 lg:grid-cols-2 items-center">
          <div>
            <h2 class="text-4xl font-bold mb-4 leading-tight">
              Our name is new<br /><span class="text-blue-500"
                >Our experience is vast</span
              >
            </h2>
            <p class="text-gray-700">
              <strong>Just who is moejoe</strong>? Some fly-by-night business
              trying to make a quick buck on the internet? Not at all. Mike
              Peritore and Josh Briley have
              <strong
                >40 years combined experience working on web based
                products</strong
              >. The team has worked together at Sports Technologies, LLC
              designing and developing fantasy sports games for NASCAR, NFL,
              PGA, and other elite sporting organizations. They also worked
              together at America's Test Kitchen, a company who has
              revolutionized the food recipe industry.
            </p>
          </div>
          <div>
            <div class="flex items-center mb-6 pb-4 border-b border-gray-200">
              <img
                src="/images/mike-fam.jpg"
                class="w-24 h-24 rounded-full mr-6"
                alt=""
              />
              <div>
                <h3 class="font-semibold text-lg mb-1">Mike Peritore</h3>
                <p class="text-gray-700">
                  Mike has been a <strong>web application developer</strong> for
                  over 20 years. He lives with his wife and children in Ludlow,
                  MA.
                </p>
              </div>
            </div>
            <div class="flex items-center">
              <img
                src="/images/josh-fam.jpg"
                class="w-24 h-24 rounded-full mr-6"
                alt=""
              />
              <div>
                <h3 class="font-semibold text-lg mb-1">Josh Briley</h3>
                <p class="text-gray-700">
                  Josh has been a
                  <strong>web designer and developer</strong> for over 20 years.
                  He lives with his wife and children in Manchester, CT.
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div id="mission" class="px-6 py-12 lg:py-24 bg-gray-800">
      <div class="container mx-auto">
        <h2 class="font-bold text-3xl text-center mb-12 text-white">
          Our mission is simple
        </h2>
        <div class="grid lg:grid-cols-3 gap-6 lg:gap-12">
          <div
            v-for="(mission, index) in missions"
            :key="index"
            :class="`border-${mission.borderColor}-400`"
            class="bg-white shadow-lg rounded-lg px-6 py-10 border-t-4 border-b-4 relative"
          >
            <h3 class="text-lg font-bold mb-2">
              {{ mission.headline }}
            </h3>
            <p class="text-gray-700">
              {{ mission.text }}
            </p>
          </div>
        </div>
      </div>
    </div>
    <div id="portfolio" class="px-6 py-12 lg:py-24">
      <div class="container mx-auto">
        <h2 class="font-bold text-3xl text-center mb-12">
          Portfolio
        </h2>
        <div class="grid lg:grid-cols-2 gap-6 lg:gap-12">
          <div
            v-for="(item, index) in porftolio"
            :key="index"
            class="shadow-lg rounded-lg flex flex-col overflow-hidden"
          >
            <div class="mb-2 p-6 bg-white">
              <img
                class="w-full h-auto"
                :src="`${item.image}?h=443&w=616`"
                alt=""
              />
            </div>
            <div
              class="p-8 bg-gray-100 flex-grow text-gray-700 border-t border-gray-200"
            >
              <h3 class="font-bold text-lg">{{ item.name }}</h3>
              <p class="mb-6">{{ item.industry }} Industry</p>
              <p class="mb-6">
                <strong>Our contribution:</strong> {{ item.text }}
              </p>
              <p class="mb-6">
                <strong>Technology used: </strong>
                <!-- eslint-disable -->
                <span
                  v-for="(tech, techindex) in item.technology"
                  :key="techindex"
                  >{{ tech
                  }}{{ item.technology.length - 1 === techindex ? '' : ',' }} </span
                >
                <!-- eslint-enable -->
              </p>
              <p v-if="item.link">
                <a
                  :href="item.link"
                  class="bg-orange-500 hover:bg-orange-600 text-white rounded font-bold py-2 px-4"
                  target="_blank"
                  >Visit Site</a
                >
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div id="contact" class="px-6 py-12 lg:py-24 bg-gray-800 text-white">
      <div class="container mx-auto">
        <div
          v-if="!formSubmitted"
          class="grid gap-6 lg:grid-cols-2 lg:gap-20 items-center"
        >
          <div>
            <svg-layout class="w-full" />
            <h2 class="text-center font-bold mt-1 text-2xl">
              Need some help with your website?
            </h2>
          </div>
          <form name="contact" netlify @submit.prevent="handleSubmit">
            <h3 class="font-bold text-3xl mb-1">
              We Can Help!
            </h3>
            <p class="mb-6">
              Do you have questions about your website? Would you like to talk
              about a new project? Feel free to reach out, and we will gladly
              respond within 24 hours.
            </p>
            <div class="form-wrapper">
              <div class="form-group">
                <label for="contact_name">Name</label>
                <input
                  id="contact_name"
                  v-model="form.contact_name"
                  type="text"
                  name="contact_name"
                  :class="{ error: appendErrorClass($v.form.contact_name) }"
                  @blur="$v.form.contact_name.$touch()"
                />
                <p v-if="$v.form.contact_name.$error" class="error-text">
                  Please enter a name
                </p>
              </div>
              <div class="form-group">
                <label for="phone">Phone Number</label>
                <input
                  id="phone"
                  v-model="form.phone"
                  type="tel"
                  name="phone"
                  :class="{ error: appendErrorClass($v.form.phone) }"
                  @blur="$v.form.phone.$touch()"
                />
                <p v-if="$v.form.phone.$error" class="error-text">
                  Please enter a phone number
                </p>
              </div>
            </div>
            <div class="form-group">
              <label for="email">Email</label>
              <input
                id="email"
                v-model="form.email"
                type="email"
                name="email"
                :class="{ error: appendErrorClass($v.form.email) }"
                @blur="$v.form.email.$touch()"
              />
              <p v-if="$v.form.email.$error" class="error-text">
                <span v-if="!$v.form.email.required">
                  Please enter an email address
                </span>
                <span v-if="!$v.form.email.email">
                  Please enter a valid email address
                </span>
              </p>
            </div>
            <div class="form-group">
              <button
                class="bg-blue-500 text-white font-bold h-12 px-6 rounded"
              >
                Submit
              </button>
            </div>
          </form>
        </div>
        <div v-else>
          <h3>Thank you!</h3>
          <p>
            Your information has been submitted to Mike and Josh at moejoe. We
            will contact you shortly.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { required, email } from 'vuelidate/lib/validators'
import axios from 'axios'
import responsiveScreens from '~/components/svg/svgResponsive'
import svgLayout from '~/components/svg/svgLayout'
export default {
  components: { responsiveScreens, svgLayout },
  data() {
    return {
      formSubmitted: false,
      form: {
        contact_name: '',
        email: '',
        phone: '',
      },
      missions: [
        {
          headline: 'Provide impeccable, unrivaled service',
          text:
            'We love what we do and we want our customers to love working with us. And we want you to tell your friends!',
          borderColor: 'blue',
        },
        {
          headline: 'Design excellent user experiences',
          text:
            "There's nothing more exciting than seeing our work being used by millions of people. We work hard to ensure that.",
          borderColor: 'orange',
        },
        {
          headline: "Develop the web's fastest websites",
          text:
            'Fast websites convert better. And we have so much fun tweeking things to make our sites blaze on the internet!',
          borderColor: 'green',
        },
      ],
      porftolio: [
        {
          name: "America's Test Kitchen",
          text:
            'Custom content management system development for search engine optimization focused content vertical pages.',
          industry: 'Food and recipe',
          technology: [
            'Ruby on Rails',
            'Postgres database',
            'Javascript',
            'HTML',
            'CSS',
            'Optimizely',
            'Google Analytics',
          ],
          link: 'https://www.americastestkitchen.com/guides/paleo',
          image:
            'https://images.ctfassets.net/xqaw6epne3xo/5Yn8RgizSco7jtjvpWQREI/e06b29acc598a5fac062dd05ff545ed7/atk-guides.jpb',
        },
        {
          name: "Cook's Illustrated",
          text: 'Website and database development for all site sections.',
          industry: 'Food and recipe',
          technology: [
            'Ruby on Rails',
            'Postgres',
            'Javascript',
            'HTML',
            'CSS',
            'Optimizely',
            'Google Analytics',
          ],
          link: 'https://www.cooksillustrated.com',
          image:
            'https://images.ctfassets.net/xqaw6epne3xo/34G5WoDtx4OjplvFUkPOD1/fb9b8ab98fdeba02d59592ee31a8981d/cooksillustrated.jpg',
        },
        {
          name: 'Berxi.com Website',
          text:
            'Development of marketing and sales focused website for Berxi.com, a division of Berkshire Hathaway Specialty Insurance. Development of web components library for insurance application and public facing products.',
          industry: 'Insurance',
          technology: [
            'Vue.js/Nuxt',
            'Contentful CMS',
            'HTML',
            'CSS',
            'Segment',
          ],
          link: 'https://www.berxi.com',
          image:
            'https://images.ctfassets.net/xqaw6epne3xo/5uuGMskvHn322O3h9dHMmL/cecde82d1cc0439b529fef4af39b33ef/berxi.jpg',
        },
        {
          name: 'IVFCryo Website',
          text:
            'Design, CMS development, and project management of the IVF Cryo company website. Auto updates to LinkedIn for each new article entry.',
          industry: 'In Vitro Fertilization',
          link: 'https://www.ivfcryo.com',
          technology: [
            'Vue.js/Nuxt',
            'Contentful CMS',
            'HTML',
            'CSS',
            'Zapier',
          ],
          image:
            'https://images.ctfassets.net/xqaw6epne3xo/6msBL3ytzS5GsJVXkt7aKt/065d8fc8532aede5924f0fcaeea0d31a/ivfcryo.jpg',
        },
        {
          name: 'PGA Dell Bracket Challenge',
          text: 'Design and development of PGA fantasy sports game',
          industry: 'Fantasy sports',
          technology: [
            'Ruby on Rails',
            'Postgres database',
            'Javascript',
            'HTML',
            'CSS',
            'Google Analytics',
          ],
          image:
            'https://images.ctfassets.net/xqaw6epne3xo/5YAeVwslsXAxQ4mnKarsyk/fe1fb136b604184fe0f6da88401a105f/PGA-BracketChallenge.jpg',
        },
        {
          name: 'Covid Fit',
          text:
            'Design and development of subscription based health and wellness membership website.',
          industry: 'Health and fitness',
          technology: [
            'Ruby on Rails',
            'Postgres database',
            'Javascript',
            'Alpine.js',
            'Web Components',
            'HTML',
            'CSS',
            'Google Analytics',
          ],
          image:
            'https://images.ctfassets.net/xqaw6epne3xo/9TVFWlsSbu2ufGvKfzbPO/6cebab7a0088c6c6e29089727a1e6571/covid-fit.jpg',
        },
        {
          name: 'NASCAR Fantasy Live Home Page',
          text:
            'Design, development, and project management of NASCAR Fantasy Sports home page.',
          industry: 'Fantasy sports',
          technology: [
            'Ruby on Rails',
            'Postgres database',
            'JQuery',
            'HTML',
            'CSS',
            'Google Analytics',
          ],
          image:
            'https://images.ctfassets.net/xqaw6epne3xo/78Qv1wQo6bpQCN0TUswojN/eb500df1d76aa9d145e9858093b98a01/nascar-fantasy-live.jpg',
        },
        {
          name: "Breeder's Cup Fantasy Sports App",
          text:
            "Design, development, and project management of the Breeder's Cup fantasy sports application.",
          industry: 'Fantasy sports',
          technology: [
            'Ruby on Rails',
            'Postgres database',
            'JQuery',
            'HTML',
            'CSS',
            'Google Analytics',
          ],
          image:
            'https://images.ctfassets.net/xqaw6epne3xo/EBvHXUWZgsoPjbbE276SD/b5e52ebac4f2a6aa294a406962e802f4/breeders-cup.jpg',
        },
      ],
    }
  },
  methods: {
    appendErrorClass(field) {
      return field.$error
    },
    encode(data) {
      return Object.keys(data)
        .map(
          (key) => `${encodeURIComponent(key)}=${encodeURIComponent(data[key])}`
        )
        .join('&')
    },
    handleSubmit() {
      if (!this.$v.form.$invalid) {
        const axiosConfig = {
          header: { 'Content-Type': 'application/x-www-form-urlencoded' },
        }
        axios.post(
          '/',
          this.encode({
            'form-name': 'contact',
            ...this.form,
          }),
          axiosConfig
        )
        this.formSubmitted = true
      }
    },
  },
  validations: {
    form: {
      contact_name: { required },
      email: {
        required,
        email,
      },
      phone: { required },
    },
  },
  head() {
    return {
      title: 'moejoe web services',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Web design and development services for your business.',
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: 'moejoe web services',
        },
        {
          hid: 'og:image',
          property: 'og:image',
          content:
            'https://images.ctfassets.net/xqaw6epne3xo/7LEcJumNuWEEpg64FTaNV9/f7053b8d3d371f01ea0fc676568eea4b/mojoesocialshare2.jpg?h=250?w=1200&h=627&fit=fill',
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content:
            'Custom web design and development services for your business.',
        },
      ],
    }
  },
}
</script>

<style>
label {
  @apply block font-bold;
}
input {
  @apply rounded h-12 px-2 w-full mt-1 text-black;
}
.form-group:not(:first-of-type) {
  @apply mt-4;
}
.error-text {
  @apply text-red-400 mt-1;
}
.border-blue-400 {
  @apply border-blue-400;
}
.border-orange-400 {
  @apply border-orange-400;
}
.border-green-400 {
  @apply border-red-400;
}
</style>
