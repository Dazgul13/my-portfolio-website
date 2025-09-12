<template>
  <section id="tools" class="text-center container-fluid">
    <div class="row text-center">
      <h2 class="section-title w-100">Tools I Use</h2>
      <div class="tool-container w-100">
        <div class="row row-cols-1 row-cols-md-3 g-4 justify-content-center text-center">

          <!-- Front End -->
          <div class="col"> 
            <h5 class="tools-subtitle">Front End</h5>
            <div class="d-flex flex-wrap gap-3 justify-content-center">
              <div class="skill-item d-flex align-items-center gap-2" title="HTML5">
                <i class="devicon-html5-plain skill-icon"></i>
                <div class="skill-label">HTML5</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="CSS3">
                <i class="devicon-css3-plain skill-icon"></i>
                <div class="skill-label">CSS3</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="Bootstrap">
                <i class="devicon-bootstrap-plain skill-icon"></i>
                <div class="skill-label">Bootstrap</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="JavaScript">
                <i class="devicon-javascript-plain skill-icon"></i>
                <div class="skill-label">JavaScript</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="DevIcon">
                <i class="devicon-devicon-plain skill-icon"></i>
                <div class="skill-label">DevIcon</div>
              </div>
            </div>
          </div>

          <!-- MERN -->
          <div class="col">
            <h5 class="tools-subtitle">MERN</h5>
            <div class="d-flex flex-wrap gap-3 justify-content-center">
              <div class="skill-item d-flex align-items-center gap-2" title="MongoDB">
                <i class="devicon-mongodb-plain skill-icon"></i>
                <div class="skill-label">MongoDB</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="Express">
                <i class="devicon-express-original skill-icon"></i>
                <div class="skill-label">Express</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="React">
                <i class="devicon-react-original skill-icon"></i>
                <div class="skill-label">React</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="React">
                <i class="devicon-vuejs-plain skill-icon"></i>
                <div class="skill-label">Vue</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="Node.js">
                <i class="devicon-nodejs-plain skill-icon"></i>
                <div class="skill-label">Node.js</div>
              </div>
            </div>
          </div>

          <!-- Other Tools -->
          <div class="col">
            <h5 class="tools-subtitle">Other Tools</h5>
            <div class="d-flex flex-wrap gap-3 justify-content-center">
              <div class="skill-item d-flex align-items-center gap-2" title="Trello">
                <i class="devicon-trello-plain skill-icon"></i>
                <div class="skill-label">Trello</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="Git">
                <i class="devicon-git-plain skill-icon"></i>
                <div class="skill-label">Git</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="Postman">
                <i class="devicon-postman-plain skill-icon"></i>
                <div class="skill-label">Postman</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="VSCode">
                <i class="devicon-vscode-plain skill-icon"></i>
                <div class="skill-label">VSCode</div>
              </div>
              <div class="skill-item d-flex align-items-center gap-2" title="Sublime Text" id="sublime">
                <img src="https://cdn.simpleicons.org/sublimetext" alt="Sublime Text" />
                <div class="skill-label">Sublime Text</div>
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
  name: "ToolsSection",
};
</script>