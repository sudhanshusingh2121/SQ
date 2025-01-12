# SQ
CREATE TABLE patients (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    diseases TEXT,
    allergies TEXT,
    room_number VARCHAR(10),
    bed_number VARCHAR(10),
    floor_number VARCHAR(10),
    age INT,
    gender VARCHAR(10),
    contact_info VARCHAR(100),
    emergency_contact VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE diet_charts (
    id SERIAL PRIMARY KEY,
    patient_id INT REFERENCES patients(id),
    meal_time VARCHAR(10), -- 'morning', 'evening', 'night'
    ingredients TEXT,
    instructions TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE pantry_staff (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    contact_info VARCHAR(100),
    location VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE delivery_personnel (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    contact_info VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE deliveries (
    id SERIAL PRIMARY KEY,
    patient_id INT REFERENCES patients(id),
    meal_time VARCHAR(10),
    delivery_personnel_id INT REFERENCES delivery_personnel(id),
    status VARCHAR(20), -- 'pending', 'delivered'
    delivery_time TIMESTAMP,
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
