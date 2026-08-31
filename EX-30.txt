// Dark mode toggle.
// Kept in its own file and its own listener so the existing
// pet-counter code in script.js is not touched.
document.addEventListener("DOMContentLoaded", function () {
  var button = document.getElementById("theme-toggle");
  var STORAGE_KEY = "theme";

  function apply(theme) {
    if (theme === "dark") {
      document.body.classList.add("dark");
      button.textContent = "Light mode";
    } else {
      document.body.classList.remove("dark");
      button.textContent = "Dark mode";
    }
  }

  // Restore the choice from the last visit.
  apply(localStorage.getItem(STORAGE_KEY) || "light");

  button.addEventListener("click", function () {
    var next = document.body.classList.contains("dark") ? "light" : "dark";
    localStorage.setItem(STORAGE_KEY, next);
    apply(next);
  });
});
