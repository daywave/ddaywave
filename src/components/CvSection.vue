<template>
  <section class="cv-section">
    <div class="content">
      <h2>My Skills</h2>
      <div class="skills-container">
        <div class="skills-column">
          <div class="skill-group" v-for="(group, index) in leftSkills" :key="index">
            <h3>{{ group.title }}</h3>
            <div class="skill" v-for="skill in group.skills" :key="skill.name">
              <span>{{ skill.name }}</span>
              <div class="skill-level">
                <div class="dot" v-for="n in 10" :key="n" :class="{ filled: n <= skill.level }"></div>
              </div>
            </div>
          </div>
        </div>
        <div class="skills-column">
          <div class="skill-group" v-for="(group, index) in rightSkills" :key="index">
            <h3>{{ group.title }}</h3>
            <div class="skill" v-for="skill in group.skills" :key="skill.name">
              <span>{{ skill.name }}</span>
              <div class="skill-level">
                <div class="dot" v-for="n in 10" :key="n" :class="{ filled: n <= skill.level }"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'CvSection',
  data() {
    return {
      leftSkills: [
        {
          title: 'Programming Languages',
          skills: [
            { name: 'C++', level: 8 },
            { name: 'Java', level: 7 },
            { name: 'JavaScript', level: 9 },
            { name: 'Python', level: 8 },
            { name: 'PHP', level: 6 },
          ]
        },
        {
          title: 'Frameworks and Libraries',
          skills: [
            { name: 'Angular', level: 7 },
            { name: 'Vue.js', level: 8 },
            { name: 'Node.js', level: 7 },
            { name: 'Express.js', level: 6 },
          ]
        }
      ],
      rightSkills: [
        {
          title: 'Web Development',
          skills: [
            { name: 'HTML', level: 9 },
            { name: 'CSS', level: 8 },
            { name: 'Bootstrap', level: 7 },
          ]
        },
        {
          title: 'Databases',
          skills: [
            { name: 'MySQL', level: 7 },
            { name: 'Elasticsearch', level: 6 },
            { name: 'HBase', level: 5 },
            { name: 'HDFS', level: 6 },
          ]
        }
      ]
    };
  }
}
</script>



<style scoped>
.cv-section {
  background-color: #000000; /* Fondo negro */
  color: #c5c8c6; /* Texto gris claro */
  padding: 4rem 2rem;
  text-align: center;
  font-family: 'Fira Code', monospace;
  overflow: hidden;
  position: relative;
}

.content {
  max-width: 1200px; /* Aumenta el ancho máximo */
  margin: 0 auto;
  position: relative;
  z-index: 2;
}

.cv-section h2 {
  font-size: 3rem;
  margin-bottom: 2rem;
  position: relative;
  color: #6DA5C0; /* Color neón */
  text-shadow: 0 0 5px #6DA5C0, 0 0 10px #6DA5C0, 0 0 20px #6DA5C0, 0 0 40px #6DA5C0, 0 0 80px #6DA5C0;
}

.skills-container {
  display: flex;
  justify-content: space-between;
  gap: 2rem;
}

.skills-column {
  flex: 1;
}

.skill-group {
  margin-bottom: 2rem;
}

.skill-group h3 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: #6DA5C0;
}

.skill {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
}

.skill span {
  flex: 1;
  text-align: left;
}

.skill-level {
  display: flex;
  gap: 0.25rem;
}

.dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background-color: #2c3e50;
  transition: background-color 0.3s;
}

.dot.filled {
  background-color: #6DA5C0; /* Color neón */
}

@media (max-width: 768px) {
  .skills-container {
    flex-direction: column;
    align-items: center;
  }
}
</style>
