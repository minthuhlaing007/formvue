<template>
  <form>
    <label for="">Email</label>
    <input type="email" required v-model="email" />
    <br /><br />
    <label for="password">Password</label>
    <input type="password" v-model="password" />
    <br /><br />
    <label for="role">Roles:</label>
    <select v-model="role">
      <option value="dev">Web Developer</option>
      <option value="dsg">Web Designer</option>
    </select>
    <div>
      <input type="checkbox" v-model="accept" />
      <label>Accept Terms and Conditions...</label>
    </div>

    <label>Check Names</label>
    <div>
      <input type="checkbox" id="name" value="minthuhlaing" v-model="names" />
      <label for="name">Min Thu Hlaing</label>
    </div>
    <div>
      <input
        type="checkbox"
        id="name1"
        value="hlainghlaingwin"
        v-model="names"
      />
      <label for="name1">hlaing hlaing win</label>
    </div>
    <div>
      <input type="checkbox" id="name2" value="winthuaung" v-model="names" />
      <label for="name2">win thu aung</label>
    </div>
    <div>
      <input type="checkbox" id="name3" value="hunnykyaw" v-model="names" />
      <label for="name3">hunny kyaw</label>
    </div>
    <br /><br />
    <div>
      <label for="">Skill</label>
      <input type="text" @keyup="addSkill" v-model="skill" />
    </div>
  </form>
  <p>{{ email }}</p>
  <p>{{ password }}</p>
  <p>{{ role }}</p>
  <p>{{ accept }}</p>
  <p>{{ names }}</p>
  <div v-for="skill in skills" :key="skill">
    <p>
      {{ skill }}
      <span class="cross" @click="deleteSkill(skill)">&#x2718;</span>
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      accept: false,
      names: [],
      skills: [],
      skill: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "Enter" && this.skill) {
        this.skills.push(this.skill);
        this.skill = "";
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((loopSkill) => {
        return loopSkill != skill;
      });
    },
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
p {
  color: navy;
  text-shadow: 10px 10px 10px crimson;
  text-transform: capitalize;
  font-style: italic;
  font-weight: bold;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin-right: 10px;
  position: relative;
  top: 2px;
}
.cross {
  cursor: pointer;
  color: darkred;
}
</style>
