<template>
    <v-container>
        <v-row align="center">
            <!-- <v-row justify="space-around"> -->
            <!-- <v-switch v-model="valid" class="ma-4" label="Valid" readonly></v-switch>
            <v-switch v-model="lazy" class="ma-4" label="Lazy"></v-switch> -->
            <!-- </v-row> -->
            <v-form
            ref="form"
            v-model="valid"
            
            >
            <v-text-field
                v-model="question"
                :rules="questionRules"
                label="Add Question"
                required
            ></v-text-field>

            <v-file-input multiple label="Select file if any(Optional)"></v-file-input>

            <v-select
                v-model="diff"
                :items="diffItems"
                :rules="[v => !!v || 'Item is required']"
                label="Select difficulty level"
                required
            ></v-select>

            <v-text-field
                v-model="minMarks"
                :rules="marksRules"
                label="Minimum marks"
                required
            ></v-text-field>

            <v-text-field
                v-model="maxMarks"
                :rules="marksRules"
                label="Maximum marks"
                required
            ></v-text-field>

            <v-select
                v-model="stream"
                :items="streamItems"
                :rules="[v => !!v || 'Item is required']"
                label="Select stream"
                required
            ></v-select>

            <v-select
                v-model="sem"
                :items="semItems"
                :rules="[v => !!v || 'Item is required']"
                label="Select semester"
                required
            ></v-select>

            <v-select
                v-model="sub"
                :items="subItems"
                :rules="[v => !!v || 'Item is required']"
                label="Select subject"
                required
            ></v-select>

            <v-checkbox
                v-model="checkbox"
                :rules="[v => !!v || 'You must agree to continue!']"
                label="Do you agree?"
                required
            ></v-checkbox>

            <v-btn
                :disabled="!valid"
                color="success"
                class="mr-4"
                @click="validate"
            >
                Validate
            </v-btn>

            <v-btn
                color="error"
                class="mr-4"
                @click="reset"
            >
                Reset Form
            </v-btn>

            <v-btn
                color="warning"
                @click="resetValidation"
            >
                Reset Validation
            </v-btn>
            </v-form>
        </v-row>
    </v-container>
</template>

<script>
export default {
    data: () => ({
        valid: true,
        question: '',
        questionRules: [
            v => !!v || 'Question is required',
            // v => (v && v.length <= 10) || 'Name must be less than 10 characters',
        ],
    //   email: '',
    //   emailRules: [
    //     v => !!v || 'E-mail is required',
    //     v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
    //   ],

        minMarks: '',
        maxMarks: '',
        marksRules: [
            v => !!v || 'Marks is required',
        ],
    
        diff: null,
        diffItems: [
            'Easy',
            'Medium',
            'Difficult',
        ],

        sem: null,
        semItems: [
            'I',
            'II',
            'III',
            'IV',
            'V',
            'VI',
            'VII',
            'VIII',
        ],

        sub: null,
        subItems: [
            'ED',
            'C++',
            'Java',
            'Python',
            'C#'
        ],

        stream: null,
        streamItems: [
            'CS',
            'EXTC',
            'Mechanical',
            'Electronics'
        ],
      checkbox: false,
    //   lazy: false,
    }),

    methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
    },
}
</script>

<style>

.container{
    min-height: 100vh;
}


</style>