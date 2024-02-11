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
