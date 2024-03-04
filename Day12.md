Let's continue our Python learning journey with Day 11, where we'll explore additional advanced topics and examples:

**Day 11: Advanced Python Topics and Tools**

1. **Concurrency with asyncio**: asyncio is a library to write concurrent code using the async/await syntax. It's particularly useful for I/O-bound tasks.

   ```python
   import asyncio

   async def main():
       print("Hello")
       await asyncio.sleep(1)
       print("World")

   asyncio.run(main())
   ```

2. **Database ORM with SQLAlchemy**: SQLAlchemy is an SQL toolkit and Object-Relational Mapping (ORM) library for Python, providing a way to interact with databases using Python objects.

   ```python
   from sqlalchemy import create_engine, Column, Integer, String
   from sqlalchemy.ext.declarative import declarative_base
   from sqlalchemy.orm import sessionmaker

   engine = create_engine('sqlite:///:memory:')
   Session = sessionmaker(bind=engine)
   session = Session()

   Base = declarative_base()

   class User(Base):
       __tablename__ = 'users'

       id = Column(Integer, primary_key=True)
       name = Column(String)

   Base.metadata.create_all(engine)

   user = User(name='Alice')
   session.add(user)
   session.commit()
   ```

3. **Web Development with FastAPI**: FastAPI is a modern, fast (high-performance), web framework for building APIs with Python 3.7+ based on standard Python type hints.

   ```python
   from fastapi import FastAPI

   app = FastAPI()

   @app.get("/")
   def read_root():
       return {"Hello": "World"}
   ```

4. **Deep Learning with TensorFlow**: TensorFlow is an open-source library for machine learning and deep learning developed by Google.

   ```python
   import tensorflow as tf

   mnist = tf.keras.datasets.mnist

   (x_train, y_train), (x_test, y_test) = mnist.load_data()
   x_train, x_test = x_train / 255.0, x_test / 255.0

   model = tf.keras.models.Sequential([
       tf.keras.layers.Flatten(input_shape=(28, 28)),
       tf.keras.layers.Dense(128, activation='relu'),
       tf.keras.layers.Dropout(0.2),
       tf.keras.layers.Dense(10)
   ])

   predictions = model(x_train[:1]).numpy()
   ```

5. **Containerization with Docker**: Docker is a set of platform as a service (PaaS) products that use OS-level virtualization to deliver software in packages called containers.

   ```Dockerfile
   FROM python:3.9

   WORKDIR /app

   COPY . .

   RUN pip install -r requirements.txt

   CMD ["python", "app.py"]
   ```

6. **Data Visualization with Dash**: Dash is a productive Python framework for building web applications.

   ```python
   import dash
   import dash_core_components as dcc
   import dash_html_components as html

   app = dash.Dash(__name__)

   app.layout = html.Div(children=[
       html.H1(children='Hello Dash'),
       html.Div(children='''
           Dash: A web application framework for Python.
       '''),
       dcc.Graph(
           id='example-graph',
           figure={
               'data': [
                   {'x': [1, 2, 3], 'y': [4, 1, 2], 'type': 'bar', 'name': 'SF'},
                   {'x': [1, 2, 3], 'y': [2, 4, 5], 'type': 'bar', 'name': u'Montréal'},
               ],
               'layout': {
                   'title': 'Dash Data Visualization'
               }
           }
       )
   ])

   if __name__ == '__main__':
       app.run_server(debug=True)
   ```

These advanced topics and tools will broaden your Python skills and enable you to tackle more complex projects. Feel free to explore them further and experiment with different use cases. Let me know if you have any questions or if you'd like to delve deeper into any specific topic!
