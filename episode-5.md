# 1. Creating React Component

## Functional component

```
import React from 'react';
import ReactDOM from 'react-dom';

const Greeting = () => {
	return <h1>First component</h1>;
};

ReactDOM.render(<Greeting />, document.getElementById('root'));

```

# 2. Class based component

```
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class Greeting extends Component {
	constructor() {
		super();
	}

	render() {
		return (
			<div>
				<h1>First component</h1>
			</div>
		);
	}
}

ReactDOM.render(<Greeting />, document.getElementById('root'));
```

