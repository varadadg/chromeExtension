import React, { useState } from "react";
import Draggable from "react-draggable";

const CircularMenu = () => {
  const [isOpen, setIsOpen] = useState(false);

  const toggleMenu = () => {
    setIsOpen(!isOpen);
  };

  return (
    <Draggable>
      <div className="flex items-center justify-center h-screen">
        <div className="relative">
          <button
            className="h-20 w-20 bg-gray-900 text-white font-bold rounded-full flex items-center justify-center absolute"
            onMouseEnter={toggleMenu}>
            {isOpen ? "opened" : "closed"}
          </button>
          {isOpen && (
            <div className="flex flex-col items-center justify-center absolute">
              <button className="h-16 w-16 bg-indigo-500 text-white font-bold rounded-full flex items-center justify-center absolute top-0 right-0">
                Admin
              </button>
              <button className="h-12 w-12 bg-indigo-500 text-white font-bold rounded-full flex items-center justify-center absolute top-0 left-24">
                User
              </button>
              <button className="h-12 w-12 bg-indigo-500 text-white font-bold rounded-full flex items-center justify-center absolute top-16 right-0">
                3
              </button>
              <button className="h-12 w-12 bg-indigo-500 text-white font-bold rounded-full flex items-center justify-center absolute bottom-0 left-0">
                4
              </button>
            </div>
          )}
        </div>
      </div>
    </Draggable>
  );
};

export default CircularMenu;




import React, { useState, useRef, useEffect } from "react";
import { createPopper, Instance } from "@popperjs/core";
import Draggable from "react-draggable";

const CircularMenu = () => {
  const [isOpen, setIsOpen] = useState(false);
  const [popperInstance, setPopperInstance] = useState<Instance | null>(null); // Define type for popperInstance
  const menuRef = useRef<HTMLDivElement>(null);
  const buttonRef = useRef<HTMLButtonElement>(null);

  useEffect(() => {
    if (isOpen && buttonRef.current && menuRef.current) {
      const popper = createPopper(buttonRef.current, menuRef.current, {
        placement: "bottom",
        modifiers: [
          {
            name: "offset",
            options: {
              offset: [0, 10], // adjust this value to position the menu as desired
            },
          },
        ],
      });
      setPopperInstance(popper);
    } else {
      if (popperInstance) {
        popperInstance.destroy();
        setPopperInstance(null);
      }
    }
    return () => {
      if (popperInstance) {
        popperInstance.destroy();
        setPopperInstance(null);
      }
    };
  }, [isOpen, popperInstance]);

  const toggleMenu = () => {
    setIsOpen(!isOpen);
  };

  return (
    <Draggable>
      <div className="flex items-center justify-center h-screen">
        <div className="relative">
          <button
            ref={buttonRef}
            className="h-20 w-20 bg-gray-900 text-white font-bold rounded-full flex items-center justify-center absolute"
            onMouseEnter={toggleMenu}>
            {isOpen ? "opened" : "closed"}
          </button>
          {isOpen && (
            <div
              ref={menuRef}
              className="flex flex-col items-center justify-center absolute">
              <button className="h-16 w-16 bg-indigo-500 text-white font-bold rounded-full flex items-center justify-center absolute top-0 right-0">
                Admin
              </button>
              <button className="h-12 w-12 bg-indigo-500 text-white font-bold rounded-full flex items-center justify-center absolute top-0 left-24">
                User
              </button>
              <button className="h-12 w-12 bg-indigo-500 text-white font-bold rounded-full flex items-center justify-center absolute top-16 right-0">
                3
              </button>
              <button className="h-12 w-12 bg-indigo-500 text-white font-bold rounded-full flex items-center justify-center absolute bottom-0 left-0">
                4
              </button>
            </div>
          )}
        </div>
      </div>
    </Draggable>

    <style>
        {`
          @keyframes jump {
            0% { 
              transform: translateY(3px);
            }
            50% { 
              transform: translateY(-15px);
            }
            100% { 
              transform: translateY(3px);
            }
          }
        `}
      </style>
  );
};

export default CircularMenu;




import React from "react";

const CircularMenu = () => {
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
      }}>
      <style>
        {`
          @keyframes jump {
            0% { 
              transform: translateY(3px);
            }
            50% { 
              transform: translateY(-15px);
            }
            100% { 
              transform: translateY(3px);
            }
          }
        `}
      </style>
      <h2
        className="tooltip relative"
        style={{
          position: "relative",
          padding: "5px",
          borderRadius: "5px",
          width: "70px",
          textAlign: "center",
          fontSize: "0.9rem",
          fontWeight: "bold",
          margin: "0 auto",
          marginBottom: "15px",
          animation: "jump 3s infinite",
          backgroundColor: "#fff",
          color: "#FA434B",
          pointerEvents: "none",
        }}>
        Look!
        <span
          style={{
            content: "''",
            position: "absolute",
            transform: "rotate(45deg)",
            display: "block",
            height: "10px",
            width: "10px",
            left: "0",
            right: "0",
            margin: "0 auto",
            backgroundColor: "inherit",
          }}></span>
      </h2>
      <div
        className="btn-pluss"
        style={{
          overflow: "hidden",
          position: "relative",
          right: "38rem",
          top: "2rem",
          display: "block",
          paddingLeft: "5px",
          paddingRight: "5px",
          borderRadius: "22px",
          width: "30px",
          margin: "0 auto",
          backgroundColor: "white",
          transition: "width .3s .5s ease, borderRadius 1.1s ease",
          cursor: "pointer",
        }}>
        <ul
          style={{
            opacity: "0",
            marginTop: "15px",
            width: "100%",
            marginLeft: "0px",
            textAlign: "center",
            fontSize: "0.9rem",
            transition: "all 1s ease",
          }}>
          <li
            style={{
              backgroundColor: "#e4e4e4",
              marginTop: "5px",
              borderRadius: "5px",
              width: "100%",
              height: "0px",
              overflow: "hidden",
              transition: "height 1s ease",
            }}>
            <a
              href="#about"
              style={{
                display: "block",
                position: "relative",
                color: "#FA434B",
                textDecoration: "none",
                overflow: "hidden",
                padding: "5px",
                borderRadius: "5px",
                transition: "all .5s ease",
              }}>
              About me
            </a>
          </li>
          <li
            style={{
              backgroundColor: "#e4e4e4",
              marginTop: "5px",
              borderRadius: "5px",
              width: "100%",
              height: "0px",
              overflow: "hidden",
              transition: "height 1s ease",
            }}>
            <a
              href="#blog"
              style={{
                display: "block",
                position: "relative",
                color: "#FA434B",
                textDecoration: "none",
                overflow: "hidden",
                padding: "5px",
                borderRadius: "5px",
                transition: "all .5s ease",
              }}>
              Blog
            </a>
          </li>
          <li
            style={{
              backgroundColor: "#e4e4e4",
              marginTop: "5px",
              borderRadius: "5px",
              width: "100%",
              height: "0px",
              overflow: "hidden",
              transition: "height 1s ease",
            }}>
            <a
              href="#projects"
              style={{
                display: "block",
                position: "relative",
                color: "#FA434B",
                textDecoration: "none",
                overflow: "hidden",
                padding: "5px",
                borderRadius: "5px",
                transition: "all .5s ease",
              }}>
              Projects
            </a>
          </li>
          <li
            style={{
              backgroundColor: "#e4e4e4",
              marginTop: "5px",
              borderRadius: "5px",
              width: "100%",
              height: "0px",
              overflow: "hidden",
              transition: "height 1s ease",
            }}>
            <a
              href="#contact"
              style={{
                display: "block",
                position: "relative",
                color: "#FA434B",
                textDecoration: "none",
                overflow: "hidden",
                padding: "5px",
                borderRadius: "5px",
                transition: "all .5s ease",
              }}>
              Contact
            </a>
          </li>
        </ul>
        <div
          style={{
            content: "'+'",
            position: "absolute",
            top: "50%",
            left: "50%",
            display: "block",
            height: "20px",
            width: "20px",
            borderRadius: "100%",
            lineHeight: "20px",
            textAlign: "center",
            fontSize: "1.1rem",
            backgroundColor: "#FA434B",
            color: "white",
            transform: "translateY(-50%) translateX(-50%)",
            transition: "all .3s .5s ease",
          }}></div>
      </div>
    </nav>
  );
};

export default CircularMenu;

