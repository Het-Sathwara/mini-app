# mini-app

A comprehensive task and analytics platform built with Python and FastAPI. This project follows an 8-week learning roadmap from absolute zero Python knowledge to a deployable SaaS backend.

## 🎯 Project Overview

This is a full-featured task management platform with:
- **Task Management**: CRUD operations for tasks
- **User Authentication**: JWT-based auth with role-based access
- **Search & Filtering**: Advanced task querying capabilities
- **Analytics**: Task completion metrics and reporting
- **Background Tasks**: Async processing for notifications
- **Deployment Ready**: Dockerized and cloud-deployable

## 📋 Complete Todo Checklist (Super Detailed for Beginners)

### **Week 1 — Python Basics & CLI**

#### **Day 1: Setup Environment**
- [x] Download Python from python.org (version 3.9+)
- [x] Install Python (check "Add to PATH" during installation)
- [x] Open terminal/command prompt, type `python --version` to verify
- [x] Download VSCode from code.visualstudio.com
- [x] Install Python extension in VSCode (search "Python" in extensions)
- [x] Install Git from git-scm.com
- [x] Create folder `task_platform` on your desktop
- [x] Open folder in VSCode (File → Open Folder)
- [x] Create file `hello.py`
- [x] Type: `print("Hello World")`
- [x] Run: Right-click → "Run Python File in Terminal"
- [x] **Success**: You see "Hello World" printed

#### **Day 2: Variables & Data Types**
- [x] Create file `variables.py`
- [x] Learn about strings: `name = "John"`
- [x] Learn about integers: `age = 25`
- [x] Learn about booleans: `is_active = True`
- [x] Learn about floats: `height = 5.9`
- [x] Print each variable: `print(name)`, `print(age)`, etc.
- [x] Try `print(f"My name is {name} and I am {age} years old")`
- [x] Run the file and see output
- [x] **Success**: All variables print correctly

#### **Day 3: Lists & Dictionaries**
- [x] Create file `data_structures.py`
- [x] Create a list: `fruits = ["apple", "banana", "orange"]`
- [x] Print the list: `print(fruits)`
- [x] Access first item: `print(fruits[0])`
- [x] Create a dictionary: `person = {"name": "John", "age": 25}`
- [x] Print dictionary: `print(person)`
- [x] Access dictionary value: `print(person["name"])`
- [x] Create list of task dictionaries:
  ```python
  tasks = [
      {"title": "Task 1", "status": "pending"},
      {"title": "Task 2", "status": "completed"}
  ]
  ```
- [x] Print all task titles using a loop:
  ```python
  for task in tasks:
      print(task["title"])
  ```
- [x] **Success**: You see both task titles printed

#### **Day 4: Loops & Conditionals**
- [x] Create file `loops_conditions.py`
- [x] Copy your tasks list from Day 3
- [x] Write a for loop to print only tasks starting with "T":
  ```python
  for task in tasks:
      if task["title"].startswith("T"):
          print(task["title"])
  ```
- [x] Try a while loop:
  ```python
  count = 0
  while count < 3:
      print(f"Count is: {count}")
      count += 1
  ```
- [x] Add more tasks to test: `{"title": "Buy groceries", "status": "pending"}`
- [x] **Success**: Only tasks starting with "T" are printed

#### **Day 5: Functions**
- [x] Create file `functions.py`
- [x] Create empty tasks list: `tasks = []`
- [x] Write function to add task:
  ```python
  def add_task(title):
      new_task = {"title": title, "status": "pending"}
      tasks.append(new_task)
      print(f"Added task: {title}")
  ```
- [x] Write function to show all tasks:
  ```python
  def show_tasks():
      for i, task in enumerate(tasks):
          print(f"{i+1}. {task['title']} - {task['status']}")
  ```
- [x] Test your functions:
  ```python
  add_task("Learn Python")
  add_task("Build API")
  show_tasks()
  ```
- [x] **Success**: Tasks are added and displayed correctly

#### **Day 6: File Input/Output**
- [ ] Create file `file_operations.py`
- [ ] Import json: `import json`
- [ ] Copy your tasks list and functions from Day 5
- [ ] Write function to save tasks to file:
  ```python
  def save_tasks():
      with open("tasks.json", "w") as file:
          json.dump(tasks, file, indent=2)
      print("Tasks saved to tasks.json")
  ```
- [ ] Write function to load tasks from file:
  ```python
  def load_tasks():
      try:
          with open("tasks.json", "r") as file:
              return json.load(file)
      except FileNotFoundError:
          return []
  ```
- [ ] Test: Add tasks, save them, restart program, load them
- [ ] **Success**: tasks.json file is created and tasks persist

#### **Day 7: Object-Oriented Programming**
- [ ] Create file `task_class.py`
- [ ] Create Task class:
  ```python
  class Task:
      def __init__(self, title, status="pending"):
          self.title = title
          self.status = status
          
      def mark_completed(self):
          self.status = "completed"
          
      def __str__(self):
          return f"{self.title} - {self.status}"
  ```
- [ ] Test your class:
  ```python
  task1 = Task("Learn OOP")
  print(task1)
  task1.mark_completed()
  print(task1)
  ```
- [ ] Create multiple task objects and store in list
- [ ] **Success**: Task objects work and can change status

### **Week 2 — FastAPI Basics**

#### **Day 8: Install FastAPI & First Endpoint**
- [ ] Open terminal in your project folder
- [ ] Create virtual environment: `python -m venv venv`
- [ ] Activate virtual environment:
  - Windows: `venv\Scripts\activate`
  - Mac/Linux: `source venv/bin/activate`
- [ ] Install FastAPI: `pip install fastapi uvicorn`
- [ ] Create file `main.py`
- [ ] Write basic FastAPI app:
  ```python
  from fastapi import FastAPI
  
  app = FastAPI()
  
  @app.get("/")
  def read_root():
      return {"message": "Hello World"}
  ```
- [ ] Run server: `uvicorn main:app --reload`
- [ ] Open browser to `http://localhost:8000`
- [ ] Open `http://localhost:8000/docs` to see automatic API docs
- [ ] **Success**: You see "Hello World" message and Swagger docs

#### **Day 9: Pydantic Models**
- [ ] Install pydantic: `pip install pydantic`
- [ ] Add to `main.py`:
  ```python
  from pydantic import BaseModel
  
  class TaskModel(BaseModel):
      title: str
      status: str = "pending"
  ```
- [ ] Create endpoint that returns a task:
  ```python
  @app.get("/sample-task")
  def get_sample_task():
      return TaskModel(title="Sample Task", status="pending")
  ```
- [ ] Test in browser: `http://localhost:8000/sample-task`
- [ ] Check the `/docs` page to see the schema
- [ ] **Success**: JSON response shows task with proper structure

#### **Day 10: GET Endpoint for Multiple Tasks**
- [ ] Create sample tasks list in `main.py`:
  ```python
  sample_tasks = [
      {"id": 1, "title": "Learn FastAPI", "status": "pending"},
      {"id": 2, "title": "Build API", "status": "completed"},
      {"id": 3, "title": "Deploy App", "status": "pending"}
  ]
  ```
- [ ] Update TaskModel to include id:
  ```python
  class TaskModel(BaseModel):
      id: int
      title: str
      status: str = "pending"
  ```
- [ ] Create GET endpoint:
  ```python
  @app.get("/tasks")
  def get_tasks():
      return sample_tasks
  ```
- [ ] Test: `http://localhost:8000/tasks`
- [ ] **Success**: All 3 tasks are returned as JSON

#### **Day 11: POST Endpoint to Create Tasks**
- [ ] Create input model:
  ```python
  class TaskCreate(BaseModel):
      title: str
      status: str = "pending"
  ```
- [ ] Create in-memory storage: `tasks_db = []`
- [ ] Add counter for IDs: `task_id_counter = 1`
- [ ] Create POST endpoint:
  ```python
  @app.post("/tasks")
  def create_task(task: TaskCreate):
      global task_id_counter
      new_task = {
          "id": task_id_counter,
          "title": task.title,
          "status": task.status
      }
      tasks_db.append(new_task)
      task_id_counter += 1
      return new_task
  ```
- [ ] Test with curl or Postman:
  ```bash
  curl -X POST "http://localhost:8000/tasks" \
       -H "Content-Type: application/json" \
       -d '{"title": "New Task"}'
  ```
- [ ] **Success**: New task is created and returned with ID

#### **Day 12: Path Parameters & Query Parameters**
- [ ] Add endpoint to get task by ID:
  ```python
  @app.get("/tasks/{task_id}")
  def get_task(task_id: int):
      for task in tasks_db:
          if task["id"] == task_id:
              return task
      return {"error": "Task not found"}
  ```
- [ ] Add search endpoint:
  ```python
  @app.get("/tasks/search")
  def search_tasks(query: str):
      results = []
      for task in tasks_db:
          if query.lower() in task["title"].lower():
              results.append(task)
      return results
  ```
- [ ] Test: `http://localhost:8000/tasks/1`
- [ ] Test: `http://localhost:8000/tasks/search?query=API`
- [ ] **Success**: Individual tasks and search results work

#### **Day 13: HTTP Status Codes**
- [ ] Import HTTPException: `from fastapi import FastAPI, HTTPException`
- [ ] Update create task to return 201:
  ```python
  from fastapi import status
  
  @app.post("/tasks", status_code=status.HTTP_201_CREATED)
  def create_task(task: TaskCreate):
      # ... existing code ...
      return new_task
  ```
- [ ] Update get task to return 404 when not found:
  ```python
  @app.get("/tasks/{task_id}")
  def get_task(task_id: int):
      for task in tasks_db:
          if task["id"] == task_id:
              return task
      raise HTTPException(status_code=404, detail="Task not found")
  ```
- [ ] Test with invalid task ID
- [ ] **Success**: Proper status codes are returned

#### **Day 14: Refactor with Routers**
- [ ] Create folder `routers`
- [ ] Create file `routers/tasks.py`
- [ ] Move task-related code to router:
  ```python
  from fastapi import APIRouter, HTTPException, status
  from pydantic import BaseModel
  
  router = APIRouter(prefix="/tasks", tags=["tasks"])
  
  # Move all task models and endpoints here
  ```
- [ ] Update `main.py`:
  ```python
  from fastapi import FastAPI
  from routers import tasks
  
  app = FastAPI()
  app.include_router(tasks.router)
  
  @app.get("/")
  def read_root():
      return {"message": "Task API is running"}
  ```
- [ ] Test all endpoints still work
- [ ] **Success**: Code is organized and all endpoints function

### **Week 3 — Database with SQLAlchemy**

#### **Day 15: Install SQLAlchemy & Database Connection**
- [ ] Install dependencies: `pip install sqlalchemy sqlite3`
- [ ] Create file `database.py`:
  ```python
  from sqlalchemy import create_engine
  from sqlalchemy.ext.declarative import declarative_base
  from sqlalchemy.orm import sessionmaker
  
  DATABASE_URL = "sqlite:///./tasks.db"
  
  engine = create_engine(DATABASE_URL, connect_args={"check_same_thread": False})
  SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)
  Base = declarative_base()
  
  def get_db():
      db = SessionLocal()
      try:
          yield db
      finally:
          db.close()
  ```
- [ ] Test connection by running the file
- [ ] **Success**: No errors, database.py runs successfully

#### **Day 16: Create Database Models**
- [ ] Create file `models.py`:
  ```python
  from sqlalchemy import Column, Integer, String, Boolean, DateTime, ForeignKey
  from sqlalchemy.orm import relationship
  from database import Base
  from datetime import datetime
  
  class User(Base):
      __tablename__ = "users"
      
      id = Column(Integer, primary_key=True, index=True)
      username = Column(String, unique=True, index=True)
      email = Column(String, unique=True, index=True)
      hashed_password = Column(String)
      is_active = Column(Boolean, default=True)
      
      tasks = relationship("Task", back_populates="owner")
  
  class Task(Base):
      __tablename__ = "tasks"
      
      id = Column(Integer, primary_key=True, index=True)
      title = Column(String, index=True)
      status = Column(String, default="pending")
      created_at = Column(DateTime, default=datetime.utcnow)
      user_id = Column(Integer, ForeignKey("users.id"))
      
      owner = relationship("User", back_populates="tasks")
  ```
- [ ] Create file `create_tables.py`:
  ```python
  from database import engine
  from models import Base
  
  Base.metadata.create_all(bind=engine)
  print("Tables created successfully!")
  ```
- [ ] Run: `python create_tables.py`
- [ ] Check that `tasks.db` file is created
- [ ] **Success**: Database file exists and no errors

#### **Day 17: CRUD - Create (POST with Database)**
- [ ] Update `routers/tasks.py` to use database:
  ```python
  from sqlalchemy.orm import Session
  from database import get_db
  from models import Task
  from fastapi import Depends
  
  @router.post("/", status_code=status.HTTP_201_CREATED)
  def create_task(task: TaskCreate, db: Session = Depends(get_db)):
      db_task = Task(title=task.title, status=task.status)
      db.add(db_task)
      db.commit()
      db.refresh(db_task)
      return db_task
  ```
- [ ] Update Pydantic models to match database:
  ```python
  class TaskResponse(BaseModel):
      id: int
      title: str
      status: str
      created_at: datetime
      
      class Config:
          orm_mode = True
  ```
- [ ] Test POST endpoint with Postman/curl
- [ ] **Success**: Task is saved to database and returned

#### **Day 18: CRUD - Read (GET from Database)**
- [ ] Update GET all tasks endpoint:
  ```python
  @router.get("/", response_model=List[TaskResponse])
  def get_tasks(db: Session = Depends(get_db)):
      tasks = db.query(Task).all()
      return tasks
  ```
- [ ] Update GET single task endpoint:
  ```python
  @router.get("/{task_id}", response_model=TaskResponse)
  def get_task(task_id: int, db: Session = Depends(get_db)):
      task = db.query(Task).filter(Task.id == task_id).first()
      if not task:
          raise HTTPException(status_code=404, detail="Task not found")
      return task
  ```
- [ ] Import List: `from typing import List`
- [ ] Test both endpoints
- [ ] **Success**: Tasks are retrieved from database

#### **Day 19: CRUD - Update (PUT to Database)**
- [ ] Create update model:
  ```python
  class TaskUpdate(BaseModel):
      title: str = None
      status: str = None
  ```
- [ ] Create PUT endpoint:
  ```python
  @router.put("/{task_id}", response_model=TaskResponse)
  def update_task(task_id: int, task_update: TaskUpdate, db: Session = Depends(get_db)):
      task = db.query(Task).filter(Task.id == task_id).first()
      if not task:
          raise HTTPException(status_code=404, detail="Task not found")
      
      if task_update.title is not None:
          task.title = task_update.title
      if task_update.status is not None:
          task.status = task_update.status
      
      db.commit()
      db.refresh(task)
      return task
  ```
- [ ] Test with Postman: PUT request to update task title/status
- [ ] **Success**: Task is updated in database

#### **Day 20: CRUD - Delete (DELETE from Database)**
- [ ] Create DELETE endpoint:
  ```python
  @router.delete("/{task_id}")
  def delete_task(task_id: int, db: Session = Depends(get_db)):
      task = db.query(Task).filter(Task.id == task_id).first()
      if not task:
          raise HTTPException(status_code=404, detail="Task not found")
      
      db.delete(task)
      db.commit()
      return {"message": "Task deleted successfully"}
  ```
- [ ] Test DELETE endpoint
- [ ] Verify task is removed from database
- [ ] **Success**: Task is deleted from database

#### **Day 21: Refactor Database Operations**
- [ ] Create folder `services`
- [ ] Create file `services/task_service.py`:
  ```python
  from sqlalchemy.orm import Session
  from models import Task
  from routers.tasks import TaskCreate, TaskUpdate
  
  def get_task(db: Session, task_id: int):
      return db.query(Task).filter(Task.id == task_id).first()
  
  def get_tasks(db: Session, skip: int = 0, limit: int = 100):
      return db.query(Task).offset(skip).limit(limit).all()
  
  def create_task(db: Session, task: TaskCreate):
      db_task = Task(title=task.title, status=task.status)
      db.add(db_task)
      db.commit()
      db.refresh(db_task)
      return db_task
  
  def update_task(db: Session, task_id: int, task_update: TaskUpdate):
      task = get_task(db, task_id)
      if task:
          if task_update.title is not None:
              task.title = task_update.title
          if task_update.status is not None:
              task.status = task_update.status
          db.commit()
          db.refresh(task)
      return task
  
  def delete_task(db: Session, task_id: int):
      task = get_task(db, task_id)
      if task:
          db.delete(task)
          db.commit()
      return task
  ```
- [ ] Update router to use service functions
- [ ] Test all endpoints still work
- [ ] **Success**: Code is organized and modular

### **Week 4 — Authentication & Users**

#### **Day 22: Password Hashing**
- [ ] Install bcrypt: `pip install python-multipart bcrypt`
- [ ] Create file `auth.py`:
  ```python
  from passlib.context import CryptContext
  
  pwd_context = CryptContext(schemes=["bcrypt"], deprecated="auto")
  
  def hash_password(password: str) -> str:
      return pwd_context.hash(password)
  
  def verify_password(plain_password: str, hashed_password: str) -> bool:
      return pwd_context.verify(plain_password, hashed_password)
  ```
- [ ] Test password hashing:
  ```python
  # Test in Python console
  from auth import hash_password, verify_password
  hashed = hash_password("mypassword")
  print(hashed)
  print(verify_password("mypassword", hashed))  # Should be True
  print(verify_password("wrongpassword", hashed))  # Should be False
  ```
- [ ] **Success**: Passwords are hashed and verified correctly

#### **Day 23: JWT Token Generation**
- [ ] Install JWT: `pip install python-jose[cryptography]`
- [ ] Add to `auth.py`:
  ```python
  from jose import JWTError, jwt
  from datetime import datetime, timedelta
  
  SECRET_KEY = "your-secret-key-here"  # Change this in production!
  ALGORITHM = "HS256"
  ACCESS_TOKEN_EXPIRE_MINUTES = 30
  
  def create_access_token(data: dict):
      to_encode = data.copy()
      expire = datetime.utcnow() + timedelta(minutes=ACCESS_TOKEN_EXPIRE_MINUTES)
      to_encode.update({"exp": expire})
      encoded_jwt = jwt.encode(to_encode, SECRET_KEY, algorithm=ALGORITHM)
      return encoded_jwt
  
  def verify_token(token: str):
      try:
          payload = jwt.decode(token, SECRET_KEY, algorithms=[ALGORITHM])
          username: str = payload.get("sub")
          if username is None:
              return None
          return username
      except JWTError:
          return None
  ```
- [ ] Test token creation and verification in Python console
- [ ] **Success**: Tokens are created and verified correctly

#### **Day 24: Register & Login Endpoints**
- [ ] Create file `routers/auth.py`:
  ```python
  from fastapi import APIRouter, HTTPException, Depends, status
  from fastapi.security import OAuth2PasswordBearer, OAuth2PasswordRequestForm
  from sqlalchemy.orm import Session
  from pydantic import BaseModel
  from database import get_db
  from models import User
  from auth import hash_password, verify_password, create_access_token
  
  router = APIRouter(prefix="/auth", tags=["authentication"])
  
  class UserCreate(BaseModel):
      username: str
      email: str
      password: str
  
  class UserResponse(BaseModel):
      id: int
      username: str
      email: str
      is_active: bool
      
      class Config:
          orm_mode = True
  
  @router.post("/register", response_model=UserResponse)
  def register(user: UserCreate, db: Session = Depends(get_db)):
      # Check if user exists
      existing_user = db.query(User).filter(User.username == user.username).first()
      if existing_user:
          raise HTTPException(status_code=400, detail="Username already registered")
      
      # Create new user
      hashed_password = hash_password(user.password)
      db_user = User(
          username=user.username,
          email=user.email,
          hashed_password=hashed_password
      )
      db.add(db_user)
      db.commit()
      db.refresh(db_user)
      return db_user
  
  @router.post("/login")
  def login(form_data: OAuth2PasswordRequestForm = Depends(), db: Session = Depends(get_db)):
      user = db.query(User).filter(User.username == form_data.username).first()
      if not user or not verify_password(form_data.password, user.hashed_password):
          raise HTTPException(status_code=401, detail="Invalid credentials")
      
      access_token = create_access_token(data={"sub": user.username})
      return {"access_token": access_token, "token_type": "bearer"}
  ```
- [ ] Add router to `main.py`: `app.include_router(auth.router)`
- [ ] Test registration and login with Postman
- [ ] **Success**: Users can register and login, receiving JWT tokens

#### **Day 25: Protect Endpoints with JWT**
- [ ] Add to `auth.py`:
  ```python
  from fastapi.security import OAuth2PasswordBearer
  
  oauth2_scheme = OAuth2PasswordBearer(tokenUrl="auth/login")
  
  def get_current_user(token: str = Depends(oauth2_scheme), db: Session = Depends(get_db)):
      username = verify_token(token)
      if username is None:
          raise HTTPException(status_code=401, detail="Invalid token")
      
      user = db.query(User).filter(User.username == username).first()
      if user is None:
          raise HTTPException(status_code=401, detail="User not found")
      
      return user
  ```
- [ ] Update task creation to require authentication:
  ```python
  @router.post("/", status_code=status.HTTP_201_CREATED)
  def create_task(task: TaskCreate, current_user: User = Depends(get_current_user), db: Session = Depends(get_db)):
      db_task = Task(title=task.title, status=task.status, user_id=current_user.id)
      db.add(db_task)
      db.commit()
      db.refresh(db_task)
      return db_task
  ```
- [ ] Test: Try creating task without token (should fail)
- [ ] Test: Login, get token, create task with token (should work)
- [ ] **Success**: Endpoints are protected and require valid JWT

#### **Day 26: Assign Tasks to Users**
- [ ] Update TaskResponse model to include user info:
  ```python
  class TaskResponse(BaseModel):
      id: int
      title: str
      status: str
      created_at: datetime
      user_id: int
      
      class Config:
          orm_mode = True
  ```
- [ ] Update get tasks to show only current user's tasks:
  ```python
  @router.get("/", response_model=List[TaskResponse])
  def get_tasks(current_user: User = Depends(get_current_user), db: Session = Depends(get_db)):
      tasks = db.query(Task).filter(Task.user_id == current_user.id).all()
      return tasks
  ```
- [ ] Test with multiple users: each should see only their tasks
- [ ] **Success**: Tasks are properly assigned to users

#### **Day 27: Role-Based Access Control**
- [ ] Add role field to User model:
  ```python
  # In models.py, add to User class:
  role = Column(String, default="member")  # "admin" or "member"
  ```
- [ ] Create migration or recreate database with new field
- [ ] Add admin check function in `auth.py`:
  ```python
  def get_admin_user(current_user: User = Depends(get_current_user)):
      if current_user.role != "admin":
          raise HTTPException(status_code=403, detail="Admin access required")
      return current_user
  ```
- [ ] Create admin-only endpoint:
  ```python
  @router.get("/all", response_model=List[TaskResponse])
  def get_all_tasks(admin_user: User = Depends(get_admin_user), db: Session = Depends(get_db)):
      tasks = db.query(Task).all()
      return tasks
  ```
- [ ] Test with admin and regular users
- [ ] **Success**: Role-based access works correctly

#### **Day 28: Test Authentication Flow**
- [ ] Install pytest: `pip install pytest httpx`
- [ ] Create file `test_auth.py`:
  ```python
  from fastapi.testclient import TestClient
  from main import app
  
  client = TestClient(app)
  
  def test_register_user():
      response = client.post("/auth/register", json={
          "username": "testuser",
          "email": "test@example.com",
          "password": "testpassword"
      })
      assert response.status_code == 200
      assert response.json()["username"] == "testuser"
  
  def test_login_user():
      response = client.post("/auth/login", data={
          "username": "testuser",
          "password": "testpassword"
      })
      assert response.status_code == 200
      assert "access_token" in response.json()
  
  def test_protected_endpoint():
      # First login to get token
      login_response = client.post("/auth/login", data={
          "username": "testuser",
          "password": "testpassword"
      })
      token = login_response.json()["access_token"]
      
      # Use token to access protected endpoint
      response = client.post("/tasks/", 
          json={"title": "Test Task"},
          headers={"Authorization": f"Bearer {token}"}
      )
      assert response.status_code == 201
  ```
- [ ] Run tests: `pytest test_auth.py -v`
- [ ] **Success**: All authentication tests pass

### **Week 5 — Search & Filtering**

#### **Day 29: Search Tasks by Title**
- [ ] Add search endpoint to `routers/tasks.py`:
  ```python
  @router.get("/search", response_model=List[TaskResponse])
  def search_tasks(
      query: str,
      current_user: User = Depends(get_current_user),
      db: Session = Depends(get_db)
  ):
      tasks = db.query(Task).filter(
          Task.user_id == current_user.id,
          Task.title.contains(query)
      ).all()
      return tasks
  ```
- [ ] Test search: `GET /tasks/search?query=python`
- [ ] Create tasks with different titles to test
- [ ] **Success**: Search returns tasks containing the query string

#### **Day 30: Filter by Status**
- [ ] Update get_tasks endpoint to accept status filter:
  ```python
  @router.get("/", response_model=List[TaskResponse])
  def get_tasks(
      status: str = None,
      current_user: User = Depends(get_current_user),
      db: Session = Depends(get_db)
  ):
      query = db.query(Task).filter(Task.user_id == current_user.id)
      
      if status:
          query = query.filter(Task.status == status)
      
      tasks = query.all()
      return tasks
  ```
- [ ] Test: `GET /tasks?status=pending`
- [ ] Test: `GET /tasks?status=completed`
- [ ] Create tasks with different statuses to test
- [ ] **Success**: Filtering by status works correctly

#### **Day 31: Filter by User (Admin Only)**
- [ ] Add user filter for admin users:
  ```python
  @router.get("/admin/filter", response_model=List[TaskResponse])
  def filter_tasks_by_user(
      user_id: int = None,
      status: str = None,
      admin_user: User = Depends(get_admin_user),
      db: Session = Depends(get_db)
  ):
      query = db.query(Task)
      
      if user_id:
          query = query.filter(Task.user_id == user_id)
      if status:
          query = query.filter(Task.status == status)
      
      tasks = query.all()
      return tasks
  ```
- [ ] Test with admin user: `GET /tasks/admin/filter?user_id=1`
- [ ] Test access denied with regular user
- [ ] **Success**: Admin can filter tasks by any user

#### **Day 32: Combine Multiple Filters**
- [ ] Update main tasks endpoint to handle multiple filters:
  ```python
  @router.get("/", response_model=List[TaskResponse])
  def get_tasks(
      status: str = None,
      title_contains: str = None,
      limit: int = 100,
      skip: int = 0,
      current_user: User = Depends(get_current_user),
      db: Session = Depends(get_db)
  ):
      query = db.query(Task).filter(Task.user_id == current_user.id)
      
      if status:
          query = query.filter(Task.status == status)
      if title_contains:
          query = query.filter(Task.title.contains(title_contains))
      
      tasks = query.offset(skip).limit(limit).all()
      return tasks
  ```
- [ ] Test combined filters: `GET /tasks?status=pending&title_contains=python&limit=10`
- [ ] **Success**: Multiple filters work together

#### **Day 33: Sort Tasks by Date**
- [ ] Add sorting to tasks endpoint:
  ```python
  @router.get("/", response_model=List[TaskResponse])
  def get_tasks(
      status: str = None,
      title_contains: str = None,
      sort_by: str = "created_at",  # created_at, title
      sort_order: str = "desc",     # asc, desc
      limit: int = 100,
      skip: int = 0,
      current_user: User = Depends(get_current_user),
      db: Session = Depends(get_db)
  ):
      query = db.query(Task).filter(Task.user_id == current_user.id)
      
      if status:
          query = query.filter(Task.status == status)
      if title_contains:
          query = query.filter(Task.title.contains(title_contains))
      
      # Add sorting
      if sort_by == "created_at":
          if sort_order == "desc":
              query = query.order_by(Task.created_at.desc())
          else:
              query = query.order_by(Task.created_at.asc())
      elif sort_by == "title":
          if sort_order == "desc":
              query = query.order_by(Task.title.desc())
          else:
              query = query.order_by(Task.title.asc())
      
      tasks = query.offset(skip).limit(limit).all()
      return tasks
  ```
- [ ] Test sorting: `GET /tasks?sort_by=created_at&sort_order=asc`
- [ ] **Success**: Tasks are sorted correctly

#### **Day 34: Refactor Query Logic to Service**
- [ ] Update `services/task_service.py` with advanced filtering:
  ```python
  def get_tasks_with_filters(
      db: Session,
      user_id: int,
      status: str = None,
      title_contains: str = None,
      sort_by: str = "created_at",
      sort_order: str = "desc",
      skip: int = 0,
      limit: int = 100
  ):
      query = db.query(Task).filter(Task.user_id == user_id)
      
      if status:
          query = query.filter(Task.status == status)
      if title_contains:
          query = query.filter(Task.title.contains(title_contains))
      
      # Sorting logic
      if sort_by == "created_at":
          if sort_order == "desc":
              query = query.order_by(Task.created_at.desc())
          else:
              query = query.order_by(Task.created_at.asc())
      elif sort_by == "title":
          if sort_order == "desc":
              query = query.order_by(Task.title.desc())
          else:
              query = query.order_by(Task.title.asc())
      
      return query.offset(skip).limit(limit).all()
  ```
- [ ] Update router to use service function
- [ ] **Success**: Query logic is organized in service layer

#### **Day 35: Test All Search & Filter Endpoints**
- [ ] Create comprehensive test file `test_search_filter.py`:
  ```python
  from fastapi.testclient import TestClient
  from main import app
  
  client = TestClient(app)
  
  def get_auth_token():
      # Register and login to get token
      client.post("/auth/register", json={
          "username": "searchuser",
          "email": "search@example.com",
          "password": "password"
      })
      response = client.post("/auth/login", data={
          "username": "searchuser",
          "password": "password"
      })
      return response.json()["access_token"]
  
  def test_search_tasks():
      token = get_auth_token()
      headers = {"Authorization": f"Bearer {token}"}
      
      # Create test tasks
      client.post("/tasks/", json={"title": "Python Learning"}, headers=headers)
      client.post("/tasks/", json={"title": "JavaScript Basics"}, headers=headers)
      
      # Test search
      response = client.get("/tasks/search?query=Python", headers=headers)
      assert response.status_code == 200
      tasks = response.json()
      assert len(tasks) == 1
      assert "Python" in tasks[0]["title"]
  
  def test_filter_by_status():
      token = get_auth_token()
      headers = {"Authorization": f"Bearer {token}"}
      
      # Test status filter
      response = client.get("/tasks?status=pending", headers=headers)
      assert response.status_code == 200
      
  def test_combined_filters():
      token = get_auth_token()
      headers = {"Authorization": f"Bearer {token}"}
      
      # Test combined filters
      response = client.get("/tasks?status=pending&title_contains=Python", headers=headers)
      assert response.status_code == 200
  ```
- [ ] Run tests: `pytest test_search_filter.py -v`
- [ ] **Success**: All search and filter functionality is tested and working

### **Week 6 — Analytics Module**

#### **Day 36: Tasks Completed per User**
- [ ] Create file `routers/analytics.py`:
  ```python
  from fastapi import APIRouter, Depends
  from sqlalchemy.orm import Session
  from sqlalchemy import func
  from database import get_db
  from models import Task, User
  from auth import get_current_user, get_admin_user
  
  router = APIRouter(prefix="/analytics", tags=["analytics"])
  
  @router.get("/user-completion-stats")
  def get_user_completion_stats(
      current_user: User = Depends(get_current_user),
      db: Session = Depends(get_db)
  ):
      # Get stats for current user
      total_tasks = db.query(Task).filter(Task.user_id == current_user.id).count()
      completed_tasks = db.query(Task).filter(
          Task.user_id == current_user.id,
          Task.status == "completed"
      ).count()
      pending_tasks = total_tasks - completed_tasks
      
      completion_rate = (completed_tasks / total_tasks * 100) if total_tasks > 0 else 0
      
      return {
          "user_id": current_user.id,
          "username": current_user.username,
          "total_tasks": total_tasks,
          "completed_tasks": completed_tasks,
          "pending_tasks": pending_tasks,
          "completion_rate": round(completion_rate, 2)
      }
  
  @router.get("/all-users-stats")
  def get_all_users_stats(
      admin_user: User = Depends(get_admin_user),
      db: Session = Depends(get_db)
  ):
      # Get completion stats for all users
      stats = db.query(
          User.id,
          User.username,
          func.count(Task.id).label("total_tasks"),
          func.sum(func.case([(Task.status == "completed", 1)], else_=0)).label("completed_tasks")
      ).outerjoin(Task).group_by(User.id, User.username).all()
      
      result = []
      for stat in stats:
          total = stat.total_tasks or 0
          completed = stat.completed_tasks or 0
          pending = total - completed
          completion_rate = (completed / total * 100) if total > 0 else 0
          
          result.append({
              "user_id": stat.id,
              "username": stat.username,
              "total_tasks": total,
              "completed_tasks": completed,
              "pending_tasks": pending,
              "completion_rate": round(completion_rate, 2)
          })
      
      return result
  ```
- [ ] Add router to `main.py`: `app.include_router(analytics.router)`
- [ ] Test endpoints with different users and tasks
- [ ] **Success**: User completion statistics are calculated correctly

#### **Day 37: Project-Based Analytics (Optional Enhancement)**
- [ ] Add project field to Task model (optional):
  ```python
  # In models.py, add to Task class:
  project = Column(String, default="General")
  ```
- [ ] Create project analytics endpoint:
  ```python
  @router.get("/project-stats")
  def get_project_stats(
      current_user: User = Depends(get_current_user),
      db: Session = Depends(get_db)
  ):
      # Group tasks by project for current user
      stats = db.query(
          Task.project,
          func.count(Task.id).label("total_tasks"),
          func.sum(func.case([(Task.status == "completed", 1)], else_=0)).label("completed_tasks")
      ).filter(Task.user_id == current_user.id).group_by(Task.project).all()
      
      result = []
      for stat in stats:
          total = stat.total_tasks
          completed = stat.completed_tasks or 0
          pending = total - completed
          completion_rate = (completed / total * 100) if total > 0 else 0
          
          result.append({
              "project": stat.project,
              "total_tasks": total,
              "completed_tasks": completed,
              "pending_tasks": pending,
              "completion_rate": round(completion_rate, 2)
          })
      
      return result
  ```
- [ ] Test project-based analytics
- [ ] **Success**: Tasks are grouped and analyzed by project

#### **Day 38: Overall System Statistics**
- [ ] Create system-wide analytics endpoint:
  ```python
  @router.get("/system-summary")
  def get_system_summary(
      admin_user: User = Depends(get_admin_user),
      db: Session = Depends(get_db)
  ):
      # Overall system statistics
      total_users = db.query(User).count()
      active_users = db.query(User).filter(User.is_active == True).count()
      total_tasks = db.query(Task).count()
      completed_tasks = db.query(Task).filter(Task.status == "completed").count()
      pending_tasks = db.query(Task).filter(Task.status == "pending").count()
      
      # Calculate averages
      avg_tasks_per_user = total_tasks / total_users if total_users > 0 else 0
      overall_completion_rate = (completed_tasks / total_tasks * 100) if total_tasks > 0 else 0
      
      # Recent activity (tasks created in last 7 days)
      from datetime import datetime, timedelta
      week_ago = datetime.utcnow() - timedelta(days=7)
      recent_tasks = db.query(Task).filter(Task.created_at >= week_ago).count()
      
      return {
          "total_users": total_users,
          "active_users": active_users,
          "total_tasks": total_tasks,
          "completed_tasks": completed_tasks,
          "pending_tasks": pending_tasks,
          "avg_tasks_per_user": round(avg_tasks_per_user, 2),
          "overall_completion_rate": round(overall_completion_rate, 2),
          "recent_tasks_7_days": recent_tasks,
          "generated_at": datetime.utcnow()
      }
  ```
- [ ] Test system summary endpoint
- [ ] **Success**: System-wide statistics are generated

#### **Day 39: Refactor Analytics to Service Layer**
- [ ] Create file `services/analytics_service.py`:
  ```python
  from sqlalchemy.orm import Session
  from sqlalchemy import func
  from models import Task, User
  from datetime import datetime, timedelta
  
  def get_user_stats(db: Session, user_id: int):
      total_tasks = db.query(Task).filter(Task.user_id == user_id).count()
      completed_tasks = db.query(Task).filter(
          Task.user_id == user_id,
          Task.status == "completed"
      ).count()
      pending_tasks = total_tasks - completed_tasks
      completion_rate = (completed_tasks / total_tasks * 100) if total_tasks > 0 else 0
      
      return {
          "total_tasks": total_tasks,
          "completed_tasks": completed_tasks,
          "pending_tasks": pending_tasks,
          "completion_rate": round(completion_rate, 2)
      }
  
  def get_all_users_stats(db: Session):
      stats = db.query(
          User.id,
          User.username,
          func.count(Task.id).label("total_tasks"),
          func.sum(func.case([(Task.status == "completed", 1)], else_=0)).label("completed_tasks")
      ).outerjoin(Task).group_by(User.id, User.username).all()
      
      result = []
      for stat in stats:
          total = stat.total_tasks or 0
          completed = stat.completed_tasks or 0
          pending = total - completed
          completion_rate = (completed / total * 100) if total > 0 else 0
          
          result.append({
              "user_id": stat.id,
              "username": stat.username,
              "total_tasks": total,
              "completed_tasks": completed,
              "pending_tasks": pending,
              "completion_rate": round(completion_rate, 2)
          })
      
      return result
  
  def get_system_summary(db: Session):
      total_users = db.query(User).count()
      active_users = db.query(User).filter(User.is_active == True).count()
      total_tasks = db.query(Task).count()
      completed_tasks = db.query(Task).filter(Task.status == "completed").count()
      pending_tasks = db.query(Task).filter(Task.status == "pending").count()
      
      avg_tasks_per_user = total_tasks / total_users if total_users > 0 else 0
      overall_completion_rate = (completed_tasks / total_tasks * 100) if total_tasks > 0 else 0
      
      week_ago = datetime.utcnow() - timedelta(days=7)
      recent_tasks = db.query(Task).filter(Task.created_at >= week_ago).count()
      
      return {
          "total_users": total_users,
          "active_users": active_users,
          "total_tasks": total_tasks,
          "completed_tasks": completed_tasks,
          "pending_tasks": pending_tasks,
          "avg_tasks_per_user": round(avg_tasks_per_user, 2),
          "overall_completion_rate": round(overall_completion_rate, 2),
          "recent_tasks_7_days": recent_tasks,
          "generated_at": datetime.utcnow()
      }
  ```
- [ ] Update analytics router to use service functions
- [ ] **Success**: Analytics logic is organized in service layer

#### **Day 40: Average Task Completion Time**
- [ ] Add completion_date field to Task model:
  ```python
  # In models.py, add to Task class:
  completed_at = Column(DateTime, nullable=True)
  ```
- [ ] Update task completion logic to set completion date:
  ```python
  # In task service, when updating task to completed:
  if task_update.status == "completed" and task.status != "completed":
      task.completed_at = datetime.utcnow()
  ```
- [ ] Add completion time analytics:
  ```python
  def get_completion_time_stats(db: Session, user_id: int):
      completed_tasks = db.query(Task).filter(
          Task.user_id == user_id,
          Task.status == "completed",
          Task.completed_at.isnot(None)
      ).all()
      
      if not completed_tasks:
          return {"message": "No completed tasks found"}
      
      completion_times = []
      for task in completed_tasks:
          time_diff = task.completed_at - task.created_at
          completion_times.append(time_diff.total_seconds() / 3600)  # Convert to hours
      
      avg_completion_time = sum(completion_times) / len(completion_times)
      
      return {
          "total_completed_tasks": len(completed_tasks),
          "average_completion_time_hours": round(avg_completion_time, 2),
          "fastest_completion_hours": round(min(completion_times), 2),
          "slowest_completion_hours": round(max(completion_times), 2)
      }
  ```
- [ ] Test completion time calculations
- [ ] **Success**: Task completion times are tracked and analyzed

#### **Day 41: Test Analytics Endpoints**
- [ ] Create comprehensive analytics tests `test_analytics.py`:
  ```python
  from fastapi.testclient import TestClient
  from main import app
  
  client = TestClient(app)
  
  def get_auth_token(username="analyticsuser"):
      client.post("/auth/register", json={
          "username": username,
          "email": f"{username}@example.com",
          "password": "password"
      })
      response = client.post("/auth/login", data={
          "username": username,
          "password": "password"
      })
      return response.json()["access_token"]
  
  def test_user_completion_stats():
      token = get_auth_token()
      headers = {"Authorization": f"Bearer {token}"}
      
      # Create some test tasks
      client.post("/tasks/", json={"title": "Task 1", "status": "pending"}, headers=headers)
      client.post("/tasks/", json={"title": "Task 2", "status": "completed"}, headers=headers)
      
      # Test user stats
      response = client.get("/analytics/user-completion-stats", headers=headers)
      assert response.status_code == 200
      
      data = response.json()
      assert "total_tasks" in data
      assert "completed_tasks" in data
      assert "completion_rate" in data
  
  def test_system_summary_admin_only():
      # Test that regular user cannot access system summary
      token = get_auth_token("regularuser")
      headers = {"Authorization": f"Bearer {token}"}
      
      response = client.get("/analytics/system-summary", headers=headers)
      assert response.status_code == 403  # Forbidden
  ```
- [ ] Run analytics tests: `pytest test_analytics.py -v`
- [ ] **Success**: All analytics endpoints are tested and working

#### **Day 42: Add Logging to Analytics**
- [ ] Create logging configuration file `logging_config.py`:
  ```python
  import logging
  import sys
  from datetime import datetime
  
  def setup_logging():
      # Create logger
      logger = logging.getLogger("task_platform")
      logger.setLevel(logging.INFO)
      
      # Create console handler
      console_handler = logging.StreamHandler(sys.stdout)
      console_handler.setLevel(logging.INFO)
      
      # Create file handler
      file_handler = logging.FileHandler("app.log")
      file_handler.setLevel(logging.INFO)
      
      # Create formatter
      formatter = logging.Formatter(
          '%(asctime)s - %(name)s - %(levelname)s - %(message)s'
      )
      console_handler.setFormatter(formatter)
      file_handler.setFormatter(formatter)
      
      # Add handlers to logger
      logger.addHandler(console_handler)
      logger.addHandler(file_handler)
      
      return logger
  
  logger = setup_logging()
  ```
- [ ] Add logging to analytics endpoints:
  ```python
  from logging_config import logger
  
  @router.get("/user-completion-stats")
  def get_user_completion_stats(
      current_user: User = Depends(get_current_user),
      db: Session = Depends(get_db)
  ):
      logger.info(f"User {current_user.username} requested completion stats")
      
      # ... existing code ...
      
      logger.info(f"Returned stats for user {current_user.username}: {result}")
      return result
  ```
- [ ] Test that logs are generated when accessing analytics
- [ ] Check `app.log` file for log entries
- [ ] **Success**: Analytics requests and responses are logged

### **Week 7 — Background Tasks**

#### **Day 43: Learn FastAPI Background Tasks**
- [ ] Create simple background task example in `main.py`:
  ```python
  from fastapi import BackgroundTasks
  import time
  from logging_config import logger
  
  def simple_background_task(message: str):
      logger.info(f"Background task started: {message}")
      time.sleep(5)  # Simulate work
      logger.info(f"Background task completed: {message}")
  
  @app.post("/test-background")
  def test_background(background_tasks: BackgroundTasks):
      background_tasks.add_task(simple_background_task, "Test message")
      return {"message": "Background task started"}
  ```
- [ ] Test the endpoint: `POST /test-background`
- [ ] Check logs to see background task execution
- [ ] **Success**: Background task runs after response is sent

#### **Day 44: Async Analytics Updates**
- [ ] Create background task for analytics updates:
  ```python
  # In services/background_tasks.py
  from sqlalchemy.orm import Session
  from database import SessionLocal
  from logging_config import logger
  import json
  from datetime import datetime
  
  def update_analytics_cache(user_id: int):
      """Update cached analytics for a user"""
      logger.info(f"Updating analytics cache for user {user_id}")
      
      db = SessionLocal()
      try:
          # Calculate fresh analytics
          from services.analytics_service import get_user_stats
          stats = get_user_stats(db, user_id)
          
          # Save to cache file (in production, use Redis)
          cache_data = {
              "user_id": user_id,
              "stats": stats,
              "updated_at": datetime.utcnow().isoformat()
          }
          
          with open(f"cache_user_{user_id}.json", "w") as f:
              json.dump(cache_data, f)
          
          logger.info(f"Analytics cache updated for user {user_id}")
          
      except Exception as e:
          logger.error(f"Error updating analytics cache: {e}")
      finally:
          db.close()
  
  def send_task_notification(user_id: int, task_title: str, action: str):
      """Send notification about task action"""
      logger.info(f"Sending notification to user {user_id}: {action} - {task_title}")
      
      # In production, this would send email/SMS/push notification
      # For now, just log it
      notification_message = f"Task '{task_title}' was {action}"
      logger.info(f"Notification sent to user {user_id}: {notification_message}")
  ```
- [ ] Update task creation to trigger background analytics update:
  ```python
  @router.post("/", status_code=status.HTTP_201_CREATED)
  def create_task(
      task: TaskCreate,
      background_tasks: BackgroundTasks,
      current_user: User = Depends(get_current_user),
      db: Session = Depends(get_db)
  ):
      db_task = Task(title=task.title, status=task.status, user_id=current_user.id)
      db.add(db_task)
      db.commit()
      db.refresh(db_task)
      
      # Add background tasks
      background_tasks.add_task(update_analytics_cache, current_user.id)
      background_tasks.add_task(send_task_notification, current_user.id, task.title, "created")
      
      return db_task
  ```
- [ ] Test task creation and check logs for background execution
- [ ] **Success**: Analytics are updated in background after task creation

#### **Day 45: Notification System**
- [ ] Enhance notification system:
  ```python
  # In services/background_tasks.py
  def send_email_notification(email: str, subject: str, message: str):
      """Send email notification (placeholder)"""
      logger.info(f"Sending email to {email}")
      logger.info(f"Subject: {subject}")
      logger.info(f"Message: {message}")
      
      # In production, integrate with email service like SendGrid, AWS SES, etc.
      # For now, just simulate email sending
      import time
      time.sleep(2)  # Simulate email sending delay
      
      logger.info(f"Email sent successfully to {email}")
  
  def process_task_assignment(task_id: int, assigned_user_id: int, assigner_user_id: int):
      """Process task assignment notification"""
      db = SessionLocal()
      try:
          task = db.query(Task).filter(Task.id == task_id).first()
          assigned_user = db.query(User).filter(User.id == assigned_user_id).first()
          assigner = db.query(User).filter(User.id == assigner_user_id).first()
          
          if task and assigned_user and assigner:
              subject = f"New Task Assigned: {task.title}"
              message = f"You have been assigned a new task '{task.title}' by {assigner.username}"
              
              send_email_notification(assigned_user.email, subject, message)
              
              # Update analytics
              update_analytics_cache(assigned_user_id)
              
      except Exception as e:
          logger.error(f"Error processing task assignment: {e}")
      finally:
          db.close()
  ```
- [ ] Add task assignment endpoint:
  ```python
  @router.put("/{task_id}/assign")
  def assign_task(
      task_id: int,
      assigned_user_id: int,
      background_tasks: BackgroundTasks,
      current_user: User = Depends(get_current_user),
      db: Session = Depends(get_db)
  ):
      task = db.query(Task).filter(Task.id == task_id).first()
      if not task:
          raise HTTPException(status_code=404, detail="Task not found")
      
      # Check if user can assign this task (owner or admin)
      if task.user_id != current_user.id and current_user.role != "admin":
          raise HTTPException(status_code=403, detail="Cannot assign this task")
      
      task.user_id = assigned_user_id
      db.commit()
      
      # Process assignment in background
      background_tasks.add_task(
          process_task_assignment,
          task_id,
          assigned_user_id,
          current_user.id
      )
      
      return {"message": "Task assigned successfully"}
  ```
- [ ] Test task assignment and check notification logs
- [ ] **Success**: Task assignments trigger background notifications

#### **Day 46: Combine Tasks + Analytics + Background**
- [ ] Create comprehensive workflow test:
  ```python
  # In test_workflow.py
  def test_complete_task_workflow():
      token = get_auth_token("workflowuser")
      headers = {"Authorization": f"Bearer {token}"}
      
      # 1. Create task
      create_response = client.post("/tasks/", 
          json={"title": "Workflow Test Task"}, 
          headers=headers
      )
      assert create_response.status_code == 201
      task_id = create_response.json()["id"]
      
      # 2. Update task to completed
      update_response = client.put(f"/tasks/{task_id}", 
          json={"status": "completed"}, 
          headers=headers
      )
      assert update_response.status_code == 200
      
      # 3. Check analytics (wait a moment for background tasks)
      import time
      time.sleep(3)
      
      analytics_response = client.get("/analytics/user-completion-stats", headers=headers)
      assert analytics_response.status_code == 200
      
      stats = analytics_response.json()
      assert stats["completed_tasks"] >= 1
  ```
- [ ] Update task completion to trigger background tasks:
  ```python
  @router.put("/{task_id}", response_model=TaskResponse)
  def update_task(
      task_id: int,
      task_update: TaskUpdate,
      background_tasks: BackgroundTasks,
      current_user: User = Depends(get_current_user),
      db: Session = Depends(get_db)
  ):
      task = db.query(Task).filter(Task.id == task_id, Task.user_id == current_user.id).first()
      if not task:
          raise HTTPException(status_code=404, detail="Task not found")
      
      old_status = task.status
      
      if task_update.title is not None:
          task.title = task_update.title
      if task_update.status is not None:
          task.status = task_update.status
          if task_update.status == "completed" and old_status != "completed":
              task.completed_at = datetime.utcnow()
      
      db.commit()
      db.refresh(task)
      
      # Trigger background tasks
      background_tasks.add_task(update_analytics_cache, current_user.id)
      
      if task_update.status == "completed" and old_status != "completed":
          background_tasks.add_task(
              send_task_notification,
              current_user.id,
              task.title,
              "completed"
          )
      
      return task
  ```
- [ ] Test complete workflow
- [ ] **Success**: All components work together seamlessly

#### **Day 47: Email Notifications (Optional)**
- [ ] Install email dependencies: `pip install aiosmtplib email-validator`
- [ ] Create email service:
  ```python
  # In services/email_service.py
  import aiosmtplib
  from email.mime.text import MIMEText
  from email.mime.multipart import MIMEMultipart
  import os
  from logging_config import logger
  
  async def send_email_async(to_email: str, subject: str, body: str):
      """Send email asynchronously"""
      try:
          # Email configuration (use environment variables in production)
          smtp_server = os.getenv("SMTP_SERVER", "smtp.gmail.com")
          smtp_port = int(os.getenv("SMTP_PORT", "587"))
          smtp_username = os.getenv("SMTP_USERNAME", "your-email@gmail.com")
          smtp_password = os.getenv("SMTP_PASSWORD", "your-app-password")
          
          # Create message
          message = MIMEMultipart()
          message["From"] = smtp_username
          message["To"] = to_email
          message["Subject"] = subject
          
          message.attach(MIMEText(body, "plain"))
          
          # Send email
          await aiosmtplib.send(
              message,
              hostname=smtp_server,
              port=smtp_port,
              start_tls=True,
              username=smtp_username,
              password=smtp_password,
          )
          
          logger.info(f"Email sent successfully to {to_email}")
          
      except Exception as e:
          logger.error(f"Failed to send email to {to_email}: {e}")
  
  def send_email_sync(to_email: str, subject: str, body: str):
      """Synchronous wrapper for email sending"""
      import asyncio
      asyncio.run(send_email_async(to_email, subject, body))
  ```
- [ ] Update background tasks to use real email:
  ```python
  def send_task_completion_email(user_email: str, task_title: str):
      subject = f"Task Completed: {task_title}"
      body = f"""
      Congratulations! You have successfully completed the task: "{task_title}"
      
      Keep up the great work!
      
      Best regards,
      Task Platform Team
      """
      
      send_email_sync(user_email, subject, body)
  ```
- [ ] Test email functionality (configure with real SMTP settings)
- [ ] **Success**: Real email notifications are sent

#### **Day 48: Test Background Task Completion**
- [ ] Create comprehensive background task tests:
  ```python
  # In test_background_tasks.py
  import time
  import json
  import os
  
  def test_analytics_cache_update():
      token = get_auth_token("cacheuser")
      headers = {"Authorization": f"Bearer {token}"}
      
      # Create task to trigger cache update
      response = client.post("/tasks/", 
          json={"title": "Cache Test Task"}, 
          headers=headers
      )
      assert response.status_code == 201
      
      # Wait for background task
      time.sleep(3)
      
      # Check if cache file was created
      cache_files = [f for f in os.listdir(".") if f.startswith("cache_user_")]
      assert len(cache_files) > 0
      
      # Verify cache content
      with open(cache_files[0], "r") as f:
          cache_data = json.load(f)
          assert "stats" in cache_data
          assert "updated_at" in cache_data
  
  def test_notification_logging():
      token = get_auth_token("notifyuser")
      headers = {"Authorization": f"Bearer {token}"}
      
      # Create and complete task
      create_response = client.post("/tasks/", 
          json={"title": "Notification Test"}, 
          headers=headers
      )
      task_id = create_response.json()["id"]
      
      client.put(f"/tasks/{task_id}", 
          json={"status": "completed"}, 
          headers=headers
      )
      
      # Wait for background tasks
      time.sleep(3)
      
      # Check logs for notification
      with open("app.log", "r") as f:
          log_content = f.read()
          assert "Notification Test" in log_content
          assert "completed" in log_content
  ```
- [ ] Run background task tests: `pytest test_background_tasks.py -v`
- [ ] **Success**: Background tasks execute correctly and are testable

#### **Day 49: Refactor Background Tasks**
- [ ] Organize background tasks into modules:
  ```python
  # services/background_tasks/__init__.py
  from .analytics_tasks import update_analytics_cache
  from .notification_tasks import send_task_notification, process_task_assignment
  from .email_tasks import send_task_completion_email
  
  __all__ = [
      "update_analytics_cache",
      "send_task_notification", 
      "process_task_assignment",
      "send_task_completion_email"
  ]
  ```
  
  ```python
  # services/background_tasks/analytics_tasks.py
  from sqlalchemy.orm import Session
  from database import SessionLocal
  from logging_config import logger
  import json
  from datetime import datetime
  
  def update_analytics_cache(user_id: int):
      """Update cached analytics for a user"""
      logger.info(f"Updating analytics cache for user {user_id}")
      
      db = SessionLocal()
      try:
          from services.analytics_service import get_user_stats
          stats = get_user_stats(db, user_id)
          
          cache_data = {
              "user_id": user_id,
              "stats": stats,
              "updated_at": datetime.utcnow().isoformat()
          }
          
          with open(f"cache_user_{user_id}.json", "w") as f:
              json.dump(cache_data, f)
          
          logger.info(f"Analytics cache updated for user {user_id}")
          
      except Exception as e:
          logger.error(f"Error updating analytics cache: {e}")
      finally:
          db.close()
  ```
  
  ```python
  # services/background_tasks/notification_tasks.py
  from logging_config import logger
  from database import SessionLocal
  from models import Task, User
  
  def send_task_notification(user_id: int, task_title: str, action: str):
      """Send notification about task action"""
      logger.info(f"Sending notification to user {user_id}: {action} - {task_title}")
      
      notification_message = f"Task '{task_title}' was {action}"
      logger.info(f"Notification sent to user {user_id}: {notification_message}")
  
  def process_task_assignment(task_id: int, assigned_user_id: int, assigner_user_id: int):
      """Process task assignment notification"""
      db = SessionLocal()
      try:
          task = db.query(Task).filter(Task.id == task_id).first()
          assigned_user = db.query(User).filter(User.id == assigned_user_id).first()
          assigner = db.query(User).filter(User.id == assigner_user_id).first()
          
          if task and assigned_user and assigner:
              logger.info(f"Task '{task.title}' assigned to {assigned_user.username} by {assigner.username}")
              
      except Exception as e:
          logger.error(f"Error processing task assignment: {e}")
      finally:
          db.close()
  ```
- [ ] Update imports in routers to use new structure
- [ ] **Success**: Background tasks are well-organized and modular

#### **Day 50: End-to-End Testing**
- [ ] Create comprehensive end-to-end test:
  ```python
  # test_end_to_end.py
  import time
  import json
  
  def test_complete_platform_workflow():
      """Test the entire platform workflow"""
      
      # 1. User Registration
      register_response = client.post("/auth/register", json={
          "username": "e2euser",
          "email": "e2e@example.com",
          "password": "password123"
      })
      assert register_response.status_code == 200
      
      # 2. User Login
      login_response = client.post("/auth/login", data={
          "username": "e2euser",
          "password": "password123"
      })
      assert login_response.status_code == 200
      token = login_response.json()["access_token"]
      headers = {"Authorization": f"Bearer {token}"}
      
      # 3. Create Multiple Tasks
      tasks = []
      for i in range(5):
          response = client.post("/tasks/", 
              json={"title": f"E2E Task {i+1}", "status": "pending"}, 
              headers=headers
          )
          assert response.status_code == 201
          tasks.append(response.json())
      
      # 4. Complete Some Tasks
      for i in range(3):
          response = client.put(f"/tasks/{tasks[i]['id']}", 
              json={"status": "completed"}, 
              headers=headers
          )
          assert response.status_code == 200
      
      # 5. Search Tasks
      search_response = client.get("/tasks/search?query=E2E", headers=headers)
      assert search_response.status_code == 200
      assert len(search_response.json()) == 5
      
      # 6. Filter Tasks
      filter_response = client.get("/tasks?status=completed", headers=headers)
      assert filter_response.status_code == 200
      assert len(filter_response.json()) == 3
      
      # 7. Get Analytics
      time.sleep(3)  # Wait for background tasks
      analytics_response = client.get("/analytics/user-completion-stats", headers=headers)
      assert analytics_response.status_code == 200
      
      stats = analytics_response.json()
      assert stats["total_tasks"] == 5
      assert stats["completed_tasks"] == 3
      assert stats["completion_rate"] == 60.0
      
      # 8. Delete Task
      delete_response = client.delete(f"/tasks/{tasks[4]['id']}", headers=headers)
      assert delete_response.status_code == 200
      
      # 9. Verify Final State
      final_tasks = client.get("/tasks", headers=headers)
      assert len(final_tasks.json()) == 4
      
      print("✅ End-to-end test completed successfully!")
  ```
- [ ] Run end-to-end test: `pytest test_end_to_end.py -v -s`
- [ ] **Success**: Complete platform workflow works perfectly

### **Week 8 — Deployment & Final Touches**

#### **Day 51: Docker Basics**
- [ ] Create `Dockerfile`:
  ```dockerfile
  FROM python:3.9-slim
  
  WORKDIR /app
  
  # Copy requirements first for better caching
  COPY requirements.txt .
  RUN pip install --no-cache-dir -r requirements.txt
  
  # Copy application code
  COPY . .
  
  # Create database tables
  RUN python create_tables.py
  
  # Expose port
  EXPOSE 8000
  
  # Run the application
  CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
  ```
- [ ] Create `requirements.txt`:
  ```
  fastapi==0.104.1
  uvicorn==0.24.0
  sqlalchemy==2.0.23
  pydantic==2.5.0
  python-multipart==0.0.6
  python-jose[cryptography]==3.3.0
  passlib[bcrypt]==1.7.4
  aiosmtplib==3.0.1
  email-validator==2.1.0
  pytest==7.4.3
  httpx==0.25.2
  ```
- [ ] Create `.dockerignore`:
  ```
  __pycache__
  *.pyc
  *.pyo
  *.pyd
  .Python
  .pytest_cache
  .coverage
  htmlcov
  .tox
  .cache
  .venv
  venv/
  .git
  .gitignore
  README.md
  Dockerfile
  .dockerignore
  *.db
  *.log
  cache_user_*.json
  ```
- [ ] Build Docker image: `docker build -t task-platform .`
- [ ] Run container: `docker run -p 8000:8000 task-platform`
- [ ] Test API in container: `curl http://localhost:8000`
- [ ] **Success**: Application runs in Docker container

#### **Day 52: Docker Compose**
- [ ] Create `docker-compose.yml`:
  ```yaml
  version: '3.8'
  
  s
