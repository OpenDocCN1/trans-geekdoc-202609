You can rearrange the first equation, and represent it in the following way:

\(m_1 (u_1 - v_1) = m_2 (v_2 - u_2)\) (7.3)

And if you rearrange the kinetic energy equation (7.2), you get:

\(m_1 u_1^2 + m_2 u_2^2 = m_1 v_1^2 + m_2 v_2^2\) (7.4)

\(m_1 (u_1^2 - v_1^2) = m_2 (v_2^2 - u_2^2)\) (7.5)

\(m_1 (u_1 + v_1)(u_1 - v_1) = m_2 (v_2 + u_2)(v_2 - u_2)\) (7.6)

Dividing (7.6) by (7.3) gives the following:

\(u_1 + v_1 = v_2 + u_2\) (7.7)

and rearranging that you get:

\(v_2 = u_1 + v_1 - u_2\) (7.8)

If you now substitute this equation for (7.8) back into (7.1) you get:

\(m_1 u_1 + m_2 u_2 = m_1 v_1 + m_2 (u_1 + v_1 - u_2)\) (7.9)

Finally, rearranging this, you can get an equation to calculate the resultant velocity of your AI vehicle, \(v_1\), knowing only the initial velocities and masses as shown:

\(m_1 u_1 + m_2 u_2 = m_1 v_1 + m_2 u_1 + m_2 v_1 - m_2 u_2\) (7.10)

\(m_1 u_1 - m_2 u_1 + 2m_2 u_2 = v_1 (m_1 + m_2)\) (7.11)

\(v_1 = (m_1 u_1 - m_2 u_1 + 2m_2 u_2) / (m_1 + m_2)\) (7.12)

Knowing the initial and resultant velocities, you just use this loss in velocity and multiply it by a tuneable parameter as shown:

\(w = k(u - v)/u,\)

where \(w\) is the weight to add for your obstacle, \(k\) is the tuneable parameter, \(u\) is the initial velocity of the AI vehicle, and \(v\) is the resultant velocity.