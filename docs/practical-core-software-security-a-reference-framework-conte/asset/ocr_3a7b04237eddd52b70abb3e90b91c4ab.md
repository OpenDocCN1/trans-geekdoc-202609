| Element Type | Type Description | Element Symbol |
| :--- | :--- | :--- |
| External Element | An element outside your control and external to your software application but may be called to or interact with the software being modeled via an entry point. | [Rectangle] |
| Process | This represents a task that handles data within the software. This task may process or perform a task based on the data. | [Circle] |
| Multiple Processes | This is used to represent a collection of sub-processes for the data and typically indicates that another DFD will be involved in which case its sub-processes are broken down and extended into an additional DFD. | [Double Circle] |
| Data Store | This represents where data is stored but not modified. | [Two parallel lines] |
| Data Flow | This represents the movement of the data within the software and its direction of movement is represented by the arrow. | [Curved Arrow] |
| Trust Boundary | A trust boundary occurs when one component doesn't trust the component on the other side of the boundary. Trust boundaries always exist between elements running at different privilege levels. There can also be trust boundaries between different components running at the same privilege level. | [Dashed Curved Line] |