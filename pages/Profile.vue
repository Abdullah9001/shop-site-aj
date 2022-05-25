<template>
  <div class="products">
    <div class="container">
      <div class="intro h-100">
        <div class="row h-100 align-items-center">
          <div class="col-md-6 ml-3">
            <h3>Profile settings</h3>

            <p>Change your profile settings here</p>
          </div>
        </div>
      </div>

      <div class="profile-content">
        <h1 class="title">Profile</h1>

        <div class="content">
          <div class="pt-3">
            <div class="container">
              <div class="row">
                <div class="col-md-6">
                  <div class="form-group">
                    <input
                      type="text"
                      name=""
                      v-model="profile.name"
                      placeholder="Full name"
                      class="form-control"
                    />
                  </div>
                </div>

                <div class="col-md-6">
                  <div class="form-group">
                    <input
                      type="text"
                      v-model="profile.phone"
                      placeholder="Phone"
                      class="form-control"
                    />
                  </div>
                </div>

                <div class="col-md-12">
                  <div class="form-group">
                    <input
                      type="text"
                      v-model="profile.address"
                      placeholder="Address"
                      class="form-control"
                    />
                  </div>
                </div>

                <div class="col-md-8">
                  <div class="form-group">
                    <input
                      type="text"
                      v-model="profile.postCode"
                      placeholder="Postcode"
                      class="form-control"
                    />
                  </div>
                </div>

                <div class="col-md-4">
                  <div class="form-group">
                    <input
                      type="submit"
                      @click="addProfile"
                      value="Save Changes"
                      class="btn btn-primary w-100"
                    />
                  </div>
                </div>
              </div>
            </div>
          </div>
          <h1 class="title">Account settings</h1>
          <div class="pt-3">
            <div class="container">
              <div class="row">
                <div class="col-md-">
                  <div class="alert alert-info">
                    Please use the Reset password email button for reseting the
                    password. The form doens't work currently
                  </div>
                </div>
                <div class="col-md-6">
                  <div class="form-group">
                    <input
                      type="text"
                      v-model="account.name"
                      placeholder="User name"
                      class="form-control"
                    />
                  </div>
                </div>

                <div class="col-md-6">
                  <div class="form-group">
                    <input
                      type="text"
                      v-model="account.email"
                      placeholder="Email address"
                      class="form-control"
                    />
                  </div>
                </div>

                <div class="col-md-6">
                  <div class="form-group">
                    <input
                      type="text"
                      v-model="account.password"
                      placeholder="New password"
                      class="form-control"
                    />
                  </div>
                </div>

                <div class="col-md-6">
                  <div class="form-group">
                    <input
                      type="text"
                      v-model="account.confirmPassword"
                      placeholder="Confirm password"
                      class="form-control"
                    />
                  </div>
                </div>

                <div class="col-md-4">
                  <div class="form-group">
                    <input type="file" class="form-control" />
                  </div>
                </div>

                <div class="col-md-4">
                  <div class="form-group">
                    <input
                      type="submit"
                      value="Save Changes"
                      class="btn btn-primary w-100"
                    />
                  </div>
                </div>

                <div class="col-md-4">
                  <div class="form-group">
                    <input
                      type="button"
                      @click="resetPassword"
                      value="Reset password email"
                      class="btn btn-success w-100"
                    />
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'sidebar',
  data() {
    return {
      profile: {
        name: '',
        phone: '',
        address: '',
        postCode: '',
      },
      account: {
        name: '',
        email: '',
        password: '',
        confirmPassword: '',
        uploadImage: '',
      },
      show: false,
    }
  },
  methods: {
    addProfile() {
      this.$fire.firestore
        .collection('profile')
        .add(this.profile)
        .then(() => {
          this.profile = {
            name: '',
            phone: '',
            address: '',
            postCode: '',
          }
        })
        .catch((err) => {
          console.log(err)
        })
    },
    resetPassword() {
      this.$fire
        .auth
        .sendPasswordResetEmail(profile.email)
        .then(() => {
          console.log('Email sent');
        })
        .catch((err) => {
          console.log(err)
        })
    },
  },
}
</script>

<style></style>
