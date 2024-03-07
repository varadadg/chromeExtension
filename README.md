import React, { useState } from "react";

const CircularMenu = () => {
  const [expanded, setExpanded] = useState(false);

  const toggleExpansion = () => {
    setExpanded(!expanded);
  };

  return (
    <nav
      className="btn-pluss-wrapper"
      style={{
        display: "flex",
        alignItems: "center",
        justifyContent: "center",
        height: "100vh",
        background: "salmon",
        fontFamily: "sans-serif",
      }}
      onMouseEnter={toggleExpansion}
      onMouseLeave={toggleExpansion}>
      <style>
        {`
          .btn-pluss-wrapper {
            position: relative;
          }

          .btn-pluss-wrapper .btn-pluss {
            overflow: hidden;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: ${expanded ? "200px" : "30px"};
            height: ${expanded ? "auto" : "30px"};
            background-color: white;
            border-radius: ${expanded ? "10px" : "50%"};
            transition: all 0.5s ease;
          }

          .btn-pluss-wrapper .btn-pluss ul {
            opacity: ${expanded ? "1" : "0"};
            visibility: ${expanded ? "visible" : "hidden"};
            transition: all 0.5s ease;
          }

          .btn-pluss-wrapper .btn-pluss li {
            height: ${expanded ? "auto" : "0px"};
            overflow: hidden;
            transition: height 0.5s ease;
          }
        `}
      </style>
      <div className="btn-pluss">
        <ul>
          <li>
            <a
              href="#about"
              style={{
                color: "#FA434B",
                textDecoration: "none",
              }}>
              About me
            </a>
          </li>
          <li>
            <a
              href="#blog"
              style={{
                color: "#FA434B",
                textDecoration: "none",
              }}>
              Blog
            </a>
          </li>
          <li>
            <a
              href="#projects"
              style={{
                color: "#FA434B",
                textDecoration: "none",
              }}>
              Projects
            </a>
          </li>
          <li>
            <a
              href="#contact"
              style={{
                color: "#FA434B",
                textDecoration: "none",
              }}>
              Contact
            </a>
          </li>
        </ul>
        <div>+</div>
      </div>
    </nav>
  );
};

export default CircularMenu;

// contentScript.js

// Execute this script when the DOM is fully loaded
document.addEventListener("DOMContentLoaded", function() {
    // Find elements with inline styles injected by your extension
    var elementsWithInlineStyles = document.querySelectorAll('[style*="your-inline-style-property"]');

    // Iterate through the matched elements and remove the specific inline styles
    elementsWithInlineStyles.forEach(function(element) {
        // Check if the element has the specific inline style property set by your extension
        if (element.style.yourInlineStyleProperty !== undefined) {
            // Remove the specific inline style property injected by your extension
            element.style.removeProperty('yourInlineStyleProperty');
        }
    });
});

